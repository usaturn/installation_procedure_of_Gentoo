===========
fstabの修正
===========

エディタで編集する ::

  # vim /etc/fstab

例 ::


     /dev/sda2               /               reiserfs        noatime                 0 1
     /dev/sda1               none            swap            sw                      0 0
     /dev/cdrom              /mnt/cdrom      auto            noauto,ro               0 0

     shm                     /dev/shm        tmpfs           nodev,nosuid,noexec     0 0


