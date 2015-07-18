============
システム設定
============

rootのパスワードの設定
======================
::

   # passwd

ツールの起動設定
================
sshdのスタートアップ ::

   # rc-update add sshd default

シリアルコンソールの設定
========================
::

   # vim /etc/inittab

     # SERIAL CONSOLES
     s0:12345:respawn:/sbin/agetty -L 115200 ttyS0 vt100
     s1:12345:respawn:/sbin/agetty -L 115200 ttyS1 vt100

   # vim /etc/securetty

     ※ 最終行に追加
     ttyS1

* 主にiLO3やVMから接続する設定
* :doc:`他にgrub側にも設定が必要。後述 <set_bootloader>`

その他システム設定
==================
::

   # vim /etc/conf.d/keymaps
       keymap="jp106"

   # vim /etc/conf.d/hwclock
       clock="UTC"
       clock_hctosys="YES"
       clock_systohc="YES"

.. note:: hwclockについて

   # hwclock 
   2013年10月04日 16時32分27秒  -0.734808 秒 
   # hwclock --utc 
   2013年10月04日 16時32分33秒  -1.000416 秒 
   # hwclock --localtime 
   2013年10月04日 07時32分36秒  -0.594151 秒

