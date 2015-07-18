============
ディスク準備
============

現状で認識しているディスクを調べる

::

   # fdisk -l

RAID1アレイがある場合の実行例(/dev/cciss/c0d0p) ::

  Disk /dev/cciss/c0d0: 587.1 GB, 587127480320 bytes
  255 heads, 32 sectors/track, 140531 cylinders, total 1146733360 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0xad45b20c

             Device Boot      Start         End      Blocks   Id  System
  /dev/cciss/c0d0p1            2048     4196351     2097152   82  Linux swap / Solaris
  /dev/cciss/c0d0p2   *     4196352  1146733359   571268504   83  Linux

  ※アレイが存在しても、このように表示されるとは限らない

RAID1アレイがある場合の実行例(/dev/sda) ::

  Disk /dev/sda: 72.7 GB, 72746008576 bytes, 142082048 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O サイズ (最小 / 推奨): 512 バイト / 512 バイト
  ディスク識別子: 0x00000080

  デバイス ブート      始点        終点     ブロック   Id  システム
  /dev/sda1            2048     4196351     2097152   82  Linux スワップ / Solaris
  /dev/sda2   *     4196352   142082047    68942848   83  Linux


ディスクのパーティション設定をする ::

   # fdisk /dev/cciss/c0d0
   Command (m for help): p ※パーティションの確認
   Command (m for help): d ※既存パーティションの削除

   ※swap領域の作成
   Command (m for help): n
   Partition type:
      p   primary (0 primary, 0 extended, 4 free)
      e   extended
   Select (default p): p
   Partition number (1-4, default 1):
   Using default value 1
   First sector (2048-33554431, default 2048):
   Using default value 2048
   Last sector, +sectors or +size{K,M,G} (2048-33554431, default 33554431): +2G ※swapパーティションに2GB割り当てる
   Partition 1 of type Linux and of size 2 GiB is set

   Command (m for help): l ※パーティションタイプを確認 飛ばしても構わない

   Command (m for help): t ※パーティションタイプを設定
   Selected partition 1
   Hex code (type L to list codes): 82 ※ partition types を Linux swap / Solarisの 82 を打つ
   Changed system type of partition 1 to 82 (Linux swap / Solaris)

   Command (m for help): p ※/dev/vda2 のSystemに Linux swap / Solaris が表示される事を確認
   Disk /dev/vda: 17.2 GB, 17179869184 bytes, 33554432 sectors
   Units = sectors of 1 * 512 = 512 bytes
   Sector size (logical/physical): 512 bytes / 512 bytes
   I/O size (minimum/optimal): 512 bytes / 512 bytes
   Disk identifier: 0x0d3e9626
      Device Boot      Start         End      Blocks   Id  System
   /dev/vda1            2048     4196351     2097152   82  Linux swap / Solaris

   ※root領域の作成
   Command (m for help): n
   Partition type:
      p   primary (1 primary, 0 extended, 3 free)
      e   extended
   Select (default p): p
   Partition number (1-4, default 2):
   Using default value 2
   First sector (4196352-33554431, default 4196352):
   Using default value 4196352
   Last sector, +sectors or +size{K,M,G} (4196352-33554431, default 33554431):
   Using default value 33554431
   Partition 2 of type Linux and of size 14 GiB is set

   Command (m for help): a ※ブート可能にする
   Partition number (1-4): 2
   Command (m for help): p ※/dev/vda2 に * が表示される事を確認
   Disk /dev/vda: 17.2 GB, 17179869184 bytes, 33554432 sectors
   Units = sectors of 1 * 512 = 512 bytes
   Sector size (logical/physical): 512 bytes / 512 bytes
   I/O size (minimum/optimal): 512 bytes / 512 bytes
   Disk identifier: 0x0d3e9626

              Device Boot      Start         End      Blocks   Id  System
   /dev/cciss/c0d0p1            2048     4196351     2097152   82  Linux swap / Solaris
   /dev/cciss/c0d0p2   *     4196352  1146733359   571268504   83  Linux

   ※以下必要なだけ作成する
   Command (m for help): n
   Select (default p): p
   First sector (14886912-78165359, default 14886912):
   Using default value 14886912
   Last sector, +sectors or +size{K,M,G} (14886912-78165359, default 78165359): +10G

   ※変更をSAVEする
   Command (m for help): w


ディスクのフォーマットをする

::

   # mkreiserfs /dev/sda2
   # mkfs.ext4 /dev/sda2

スワップパーティションを初期化、有効化する

::

   # mkswap /dev/sda1
   # swapon -v /dev/sda1

ディスクのマウント::

   # mkdir -p /mnt/gentoo/boot/grub
   # mount /dev/sda2 /mnt/gentoo
     or # mount /dev/vda2 /mnt/gentoo

.. note:: 2TB以上のボリュームを作成する場合

   ``parted`` コマンドを利用してパーティションを作成する。

   ::

      # パーティションの確認
      (parted) print

      # 不要なパーティションの削除
      (parted) rm [番号]

      # 2TB以上のボリュームを作成する場合はgptラベルを貼る
      (parted) mklabel gpt

      # ext4で先頭500MBからディスクの最後までを使用する場合
      (parted) mkpart primary ext4 500 -1s

      # reiserfsでディスク全てを使用する場合
      (parted)  mkpart primary reiserfs 0% 100%

.. note:: ディスクが元々GPTだった場合

   fdiskを実施するとGPTモードになってしまう。そのまま実施するとGPTディスクになりgrubの設定で躓く事がある。

       gdisk


       root@sysresccd /root % gdisk /dev/sda
       Command (? for help): r

       Recovery/transformation command (? for help): g

       MBR command (? for help): ?

       MBR command (? for help): a
       Toggle active flag for partition: 2

       MBR command (? for help): p   #確認

       MBR command (? for help): w   #

       Converted 3 partitions. Finalize and exit? (Y/N): y
       Warning: The kernel is still using the old partition table.
       The new table will be used at the next reboot.
       GPT data structures destroyed! You may now partition the disk using fdisk or
       other utilities.





       root@sysresccd /root %
       root@sysresccd /root % gdisk /dev/sda
       GPT fdisk (gdisk) version 0.8.10

       Partition table scan:
         MBR: protective
         BSD: not present
         APM: not present
         GPT: present

       Found valid GPT with protective MBR; using GPT.

       Command (? for help): g
       b       back up GPT data to a file
       c       change a partition's name
       d       delete a partition
       i       show detailed information on a partition
       l       list known partition types
       n       add a new partition
       o       create a new empty GUID partition table (GPT)
       p       print the partition table
       q       quit without saving changes
       r       recovery and transformation options (experts only)
       s       sort partitions
       t       change a partition's type code
       v       verify disk
       w       write table to disk and exit
       x       extra functionality (experts only)
       ?       print this menu

       Command (? for help): r

       Recovery/transformation command (? for help): g

       MBR command (? for help): ?
       a       toggle the active/boot flag
       c       recompute all CHS values
       l       set partition as logical
       o       omit partition
       p       print the MBR partition table
       q       quit without saving changes
       r       set partition as primary
       s       sort MBR partitions
       t       change partition type code
       w       write the MBR partition table to disk and exit

       MBR command (? for help): p

       ** NOTE: Partition numbers do NOT indicate final primary/logical status,
       ** unlike in most MBR partitioning tools!

       ** Extended partitions are not displayed, but will be generated as required.

       Disk size is 1953525168 sectors (931.5 GiB)
       MBR disk identifier: 0x00000000
       MBR partitions:

                                                          Can Be   Can Be
       Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
          1                  2048     16779263   primary     Y        Y      0x82
          2              16779264     58722303   primary              Y      0x83
          3              58722304   1953525134   primary              Y      0x8E

       MBR command (? for help): a
       Toggle active flag for partition: 2

       MBR command (? for help): p

       Disk size is 1953525168 sectors (931.5 GiB)
       MBR disk identifier: 0x00000000
       MBR partitions:

                                                          Can Be   Can Be
       Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
          1                  2048     16779263   primary     Y        Y      0x82
          2      *       16779264     58722303   primary              Y      0x83
          3              58722304   1953525134   primary              Y      0x8E

       MBR command (? for help):

       MBR command (? for help):

       MBR command (? for help):

       MBR command (? for help): ?
       a       toggle the active/boot flag
       c       recompute all CHS values
       l       set partition as logical
       o       omit partition
       p       print the MBR partition table
       q       quit without saving changes
       r       set partition as primary
       s       sort MBR partitions
       t       change partition type code
       w       write the MBR partition table to disk and exit

       MBR command (? for help): g
       a       toggle the active/boot flag
       c       recompute all CHS values
       l       set partition as logical
       o       omit partition
       p       print the MBR partition table
       q       quit without saving changes
       r       set partition as primary
       s       sort MBR partitions
       t       change partition type code
       w       write the MBR partition table to disk and exit

       MBR command (? for help): s

       MBR command (? for help): w

       Converted 3 partitions. Finalize and exit? (Y/N): y
       Warning: The kernel is still using the old partition table.
       The new table will be used at the next reboot.
       GPT data structures destroyed! You may now partition the disk using fdisk or
       other utilities.




