.. _toppage:

==============================
Gentoo/Linuxのインストール手順
==============================

前提条件
========

:HW: PC/AT互換機
:CPU: x86_x64
:NW: DHCPでIPaddrが割り当てられるLANに接続できる事
:Media: 下記よりISOイメージをダウンロードし、光学メディアに焼きこむかブータブルUSBメモリを作成する事

   http://www.sysresccd.org/Download

   ファイル名: systemrescuecd-x86-x.x.x.iso


詳細手順
========

.. toctree::
   :maxdepth: 2

   default/preparing_to_install
   default/preparing_to_disk
   default/preparing_to_install_file
   default/rewrite_makeconf
   default/preparing_to_chroot
   default/preparing_to_compile_kernel
   default/grasp_system
   default/compile_kernel
   default/rewrite_fstab
   default/config_gentoo_network
   default/set_system
   default/install_package
   default/set_bootloader
   default/reboot_system
   default/package_for_default


