========================
カーネルをコンパイルする
========================

Gentooのカーネルソースをインストール
====================================
::

  # emerge -avt gentoo-sources
  # ls -l /usr/src

カーネルコンパイルのconfig設定
===============================
::

  # cd /usr/src/linux
  # make menuconfig


make menuconfigのKVM用パラメータ
--------------------------------

Linux/x86 3.17.8-gentoo-r1 Kernel Configuration ::

  [*] Enable loadable module support  --->
    [*]   Forced module loading
    [*]   Module unloading
    [*]     Forced module unloading
    [*]   Module versioning support
    [ ]   Source checksum for all modules (NEW)
    [ ]   Module signature verification (NEW)

  Processor type and features  --->
    [*] Linux guest support  --->
      [*]   Enable paravirtualization code ※KVM Guest
      [*]     Paravirtualization layer for spinlocks ※KVM Guest
      [ ]     Xen guest support
      [*]   KVM Guest support (including kvmclock) ※KVM Guest
      [*]   Paravirtual steal time accounting

    Processor family (Generic-x86-64)  --->
     (X) Core 2/newer Xeon

    <*> CPU microcode loading support ※ CPUのマイクロコードアップデートに必要
    [*]   Intel microcode loading support ※ CPUのマイクロコードアップデートに必要


  [*] Networking support  --->
    Networking options  --->
      <M>   IP: AH transformation ※iptables
      <M>   IP: ESP transformation ※iptables
      <M>   IP: IPComp transformation ※iptables
      <M>   IP: IPsec transport mode ※iptables
      <M>   IP: IPsec tunnel mode ※iptables
      <M>   IP: IPsec BEET mode ※iptables
      <*>   Large Receive Offload (ipv4/tcp) (NEW) ※iptables
      <*>   INET: socket monitoring interface ※iptables
      <M>     UDP: socket monitoring interface ※iptables
      <*>   The IPv6 protocol  ---> ※iptables
      [*] Network packet filtering framework (Netfilter)  ---> ※iptables
        [*]   Advanced netfilter configuration
              Core Netfilter Configuration  ---> ※iptables
                <*>   nfmark target and match support
                <*>   ctmark target and match support
                <*>   CHECKSUM target support
                <*>   "addrtype" address type match support
                <*>   "comment" match support 
                <*>   "conntrack" connection tracking match support
                <*>   "hl" hoplimit/TTL match support
                <*>   "iprange" address range match support
                <*>   "length" match support
                <*>   "limit" match support
                <*>   "mac" address match support
                <*>   "multiport" Multiple port match support
             IP: Netfilter Configuration  --->
                <*> IP tables support (required for filtering/masq/NAT)
                <*>   "ah" match support
                <*>   "ecn" match support
                <*>   "rpfilter" reverse path filter match support
                <*>   "ttl" match support
                <*>   IPv4 NAT
                <*>     MASQUERADE target support
                <*>     NETMAP target support
                <*>     REDIRECT target suppor
                <*> ARP tables support
                <*>   ARP packet filtering
                <*>   ARP payload mangling
        <*>   Ethernet Bridge tables (ebtables) support  ---> ※802.1d Ethernet Bridgingを先にチェック
          <*>   ebt: mark target support
      <*> 802.1d Ethernet Bridging ※VMが使用するインターフェースブリッジで使用
      [*]   IGMP/MLD snooping (NEW)
      [*]   VLAN filtering
      <*> 802.1Q/802.1ad VLAN Support ※VMが使用するインターフェースブリッジで使用
      [*]   GVRP (GARP VLAN Registration Protocol) support ※VMが使用するインターフェースブリッジで使用
      [*]   MVRP (Multiple VLAN Registration Protocol) support ※VMが使用するインターフェースブリッジで使用
    [ ]   Amateur Radio support  --->
    < >   RF switch subsystem support  --->
    <*>   Plan 9 Resource Sharing Support (9P2000)  --->  ※KVMゲスト VirtFSに必要 Virtualization driversを先にチェック
      <*>   9P Virtio Transport  ※KVMゲスト VirtFSに必要 Virtualization driversを先にチェック
    <*>   CAIF support  --->

  Device Drivers  --->
    [*] Block devices  --->
      <*>   DRBD Distributed Replicated Block Device support ※DRBDを使う場合
      [*]     DRBD fault injection ※DRBDを使う場合
      <*>   Virtio block driver ※KVMゲスト必須 Virtio driversを先にチェック

    SCSI device support  --->
      [*] SCSI low-level drivers  ---> ※サーバでLSIのRAIDカードを使っている場合
          [*]   LSI Logic New Generation RAID Device Drivers
          <*>     LSI Logic Management Module (New Driver)
          <*>       LSI Logic MegaRAID Driver (New Driver)
          <*>   LSI Logic Legacy MegaRAID Driver
          <*>   LSI Logic MegaRAID SAS RAID Module
          <*>   virtio-scsi support (EXPERIMENTAL) ※KVMゲスト

    [*] Multiple devices driver support (RAID and LVM)  ---> ※LVMを使う場合
      <*>   Device mapper support
      <*>     Crypt target support
      <*>     Snapshot target
      <*>     Thin provisioning target
      <*>     Mirror target
      <*>   Multipath target
         <*>     I/O Path Selector based on the number of in-flight I/Os
         <*>     I/O Path Selector based on the service time

    [*] Network device support  --->
      <M>   Bonding driver support ※複数のインターフェースをまとめる場合
      <*>     MAC-VLAN support
      <*>       MAC-VLAN based tap driver
      <*>   Universal TUN/TAP device driver support ※KVMホスト
      <*>     Virtio network driver ※KVMゲスト 必須
      <*>   CAIF virtio transport driver ※KVMホスト 先に Networking support ->  CAIF support をチェックする必要あり
        <*>     Host kernel accelerator for virtio net ※KVMホスト
      [*]   Ethernet driver support  ---> ※必要に応じて
          [*]   Broadcom devices
          {*}   Broadcom NetXtremeII support

    Character devices  --->
      <*> Virtio console  ※KVMゲスト device virtio-serial を使ったシリアル接続をする時に必要 libvirtのシリアル接続には不要
      <*> Hardware Random Number Generator Core support  --->
          <*>   VirtIO Random Number Generator support※KVMゲスト
      Serial drivers  --->
        <*> 8250/16550 and compatible serial support ※シリアル接続に必要
        [*]   Console on 8250/16550 and compatible serial port ※シリアル接続に必要

    Graphics support  --->
        Direct Rendering Manager  --->
            <*> Kernel modesetting driver for MGA G200 server engines ※サーバのグラフィックカードで使われている事が多い lspciの結果を見る
            <*> ATI Radeon
              [*]   Enable userspace modesetting on radeon (DEPRECATED)

    [*] DMA Engine support  --->
       <*>   Intel I/OAT DMA support

    [*] Virtualization drivers  ---> ※KVMホスト
    Virtio drivers  ---> ※KVMホスト
      <*> PCI driver for virtio devices ※KVMホスト
      <*> Virtio balloon driver ※KVMホスト
      <*> Platform bus driver for memory mapped virtio devices ※KVMホスト
      [*]   Memory mapped virtio devices parameter parsing ※KVMホスト

  Firmware Drivers  --->
    <*> BIOS update support for DELL systems via sysfs
    <*> Dell Systems Management Base Driver

  File systems  --->
    [*]   Ext3 extended attributes (NEW)
    <*> The Extended 4 (ext4) filesystem
      [*]   Use ext4 for ext2/ext3 file systems
      [*]   Ext4 POSIX Access Control Lists
      [*]   Ext4 Security Labels ※KVMホスト

    [*] Dnotify support ※NFSを利用する時に必要
    [*] Network File Systems  --->
       <*>     NFS client support for NFS version 4
       [*]   NFS client support for NFSv4.1
       <*>   NFS server support ※NFSサーバを構築する場合
       -*-     NFS server support for NFS version 3
       [*]     NFS server support for NFS version 4
       [*]       Provide Security Label support for NFSv4 server
       <*>   Plan 9 Resource Sharing Support (9P2000) ※KVMゲスト VirtFS
       [*]     9P POSIX Access Control Lists ※KVMゲスト VirtFS
       [*]     9P Security Labels ※KVMゲスト VirtFS


  Security options  --->
    [ ] Enable different security models

  -*- Cryptographic API  --->
    <*>   CRC32c INTEL hardware acceleration
    <*>   GHASH digest algorithm (CLMUL-NI accelerated)
    <*>   AES cipher algorithms (x86_64)

  [*] Virtualization  --->
     <*>   Kernel-based Virtual Machine (KVM) support ※KVMホスト
       <*>     KVM for Intel processors support ※KVMホスト
       < >     KVM for AMD processors support
       [ ]     Audit KVM MMU (NEW)
       [*]     KVM legacy PCI device assignment support (NEW) ※KVMホスト
       <*>   Host kernel accelerator for virtio net ※KVMホスト


カーネルをインストールする
==========================
カーネルconfigが終わったらコンパイル、インストールを実施する ::

  # make && make modules_install
  # make install

起動時モジュール読み込み
========================
カーネルconfigでモジュールは強制的に読み込ませているが、引数が必要なモジュールは別途設定が必要 ::

  # vim /etc/conf.d/modules

   modules_3="${modules_3} bonding"
   module_bonding_args_3="mode=1 miimon=200"

  # 参考 find /lib/modules/*gentoo*/ -type f -iname '*.o' -or -iname '*.ko' | awk -F"/" -v q='"' '{gsub(/\.ko$/,"",$NF);printf "modules=\"%s\"\n" ,$NF}'

