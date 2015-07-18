================
システムの再起動
================
* リブートする前にchrootを抜けmountした領域を外す

::

   # exit
   # cd
   # umount -l /mnt/gentoo/dev{/shm,/pts,}
   # umount -l /mnt/gentoo/proc
   # reboot


一度、shutdownした後、やり直す時に必要なコマンド ::

  # mkdir /mnt/gentoo/boot
  # mount /dev/vda2 /mnt/gentoo
  # mount -t proc none /mnt/gentoo/proc
  # mount --rbind /sys /mnt/gentoo/sys
  # mount --rbind /dev /mnt/gentoo/dev
  # cd /mnt/gentoo && chroot /mnt/gentoo /bin/bash
  # env-update
  # source /etc/profile && export PS1="(chroot) $PS1"
  # mount -a

  # vim /etc/portage/make.conf


