======================
OSインストール後の設定
======================

システムアップデート
====================
OSインストール直後でもOpenSSHやOpenSSL等のアップデートがある為、全てアップデートをかける ::

   ※ Pythonをsqlite込みで再ビルド
   # echo "dev-lang/python sqlite gdbm ipv6 ncurses readline ssl threads xml" >> /etc/portage/package.use/python
   # emerge -avt python
   # emerge -avt openssh
   # emerge --update --deep @world # 最新である事を確認

NTPの設定
=========
::

   # echo "net-misc/ntp vim-syntax" >> /etc/portage/package.use/ntp
   # emerge -avt net-misc/ntp
   # vim /etc/ntp.conf
     server ntp.nict.jp  # 適宜
   # ntpdate 203.138.206.61
   # ntpdate 192.168.1.200
   # /etc/init.d/ntpd start
   # ntpq -p
   # rc-update add ntpd default

デフォルトエディタの設定
========================
::

    # vim /etc/profile
        EDITOR=/usr/bin/vim
        export EDITOR=${EDITOR:-/bin/nano} # この行の上に追加
    # . /etc/profile

sudoの設定
==========
::

  # emerge -avt app-admin/sudo
  # visudo
    %wheel ALL=(ALL) ALL

  # ワンライナーで書き換え ※要リスタート
  # perl -i.ori -pe 's/^# (%wheel.+\) ALL)$/\1\n%techteam ALL=\(ALL\) ALL/g' /etc/sudoers

sshdの設定
==========
::

  # vim /etc/ssh/sshd_config
    PermitRootLogin no         # rootログイン不可
    UsePAM no                  # パスワード認証不可
    RSAAuthentication no       # ssh v1 不可
    PubkeyAuthentication yes   # ssh v2 許可

NFSマウント
===========

標準のNFS領域をマウントする ::

  # emerge -avt net-fs/nfs-utils
  # rc-update add nfsclient default
  # mkdir -p /export/work_data
  # /etc/init.d/nfsclient start
  # vim /etc/fstab
    ※ nfsの記述を有効にする
  # mount -a
  # df -h

Pythonのバージョン指定
======================
::

   # vim /etc/portage/make.conf
     PYTHON_TARGETS="python2_7"

   # eselect python set 1
   # eselect python list
     Available Python interpreters:
       [1]   python2.7 *
       [2]   python3.3
       [3]   python3.4

Intel CPUのマイクロコード自動アップデート ::

  # emerge -avt microcode-ctl
  # /etc/init.d/microcode_ctl start
  # rc-update add microcode_ctl boot

その他パッケージインストール
============================

システムユーティリティ ::

  # emerge -avt app-portage/eix
  # eix-update

一括インストール ::

  # emerge -avt app-portage/gentoolkit mlocate net-dns/bind-tools app-misc/screen net-misc/curl sys-apps/dstat app-portage/pfl

equery ::

  # emerge -avt app-portage/gentoolkit

e-file ::

  # app-portage/pfl

locate::

  # emerge -avt mlocate

DNSユーティリティ(nslookup他) ::

  # emerge -avt net-dns/bind-tools

screen ::

  # emerge -avt app-misc/screen

curl ::

  # emerge -avt net-misc/curl

リソース表示コマンド ::

  # emerge -avt sys-apps/dstat


作業後の確認
============
インストールしたパッケージの確認 ::

  # eix -cI --selected

スタートアップの確認 ::

  # rc-update show
  # rc-status -a

