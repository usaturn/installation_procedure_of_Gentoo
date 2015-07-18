============
chrootの準備
============

DNS情報のコピー
===============
::

   # cp -L /etc/resolv.conf /mnt/gentoo/etc/

システムパーティションのマウント
================================
::

   # mount -t proc none /mnt/gentoo/proc
   # mount --rbind /sys /mnt/gentoo/sys
   # mount --rbind /dev /mnt/gentoo/dev

chrootする
===========
::

   # cd /mnt/gentoo && chroot /mnt/gentoo /bin/bash
   # env-update
   # source /etc/profile && export PS1="(chroot) $PS1"


