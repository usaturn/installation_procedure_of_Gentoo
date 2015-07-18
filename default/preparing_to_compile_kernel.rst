===================
Portageツリーの更新
===================

webrsyncの実行
==============
* 事前に直接ダウンロード、展開をしているのならば不要

::

   # mkdir /usr/portage
   # emerge-webrsync
       # emerge --oneshot portage
       ※ 新しいバージョンがあると警告された場合

Gentoo側で変更のあったインストール時の注意事項を閲覧
====================================================
::

   # eselect news list
   # eselect news read

profileの変更
=============
標準設定で問題無いので設定不要 ::

   # eselect profile list

        Available profile symlink targets:
          [1]   default/linux/amd64/13.0 *
          [2]   default/linux/amd64/13.0/selinux
          [3]   default/linux/amd64/13.0/desktop
          [4]   default/linux/amd64/13.0/desktop/gnome
          [5]   default/linux/amd64/13.0/desktop/kde
          [6]   default/linux/amd64/13.0/developer
          [7]   default/linux/amd64/13.0/no-multilib
          [8]   default/linux/amd64/13.0/x32
          [9]   hardened/linux/amd64
          [10]  hardened/linux/amd64/selinux
          [11]  hardened/linux/amd64/no-multilib
          [12]  hardened/linux/amd64/no-multilib/selinux
          [13]  hardened/linux/amd64/x32
          [14]  hardened/linux/uclibc/amd64

   # eselect profile set 1 # 例

※失敗する時はPortageツリーの更新を失敗しているので確認する事

Vimのインストール(作業の為)
===========================
::

   # echo app-editors/vim python vim-pager >> /etc/portage/package.use/vim
   # emerge -avt app-editors/vim


ロケールの設定
==============
::

  ※ロケールの指定
  # vim /etc/locale.gen
     ja_JP.UTF-8 UTF-8
     or
     # sed -i.bak -r 's/#(ja_JP\.UTF-8 UTF-8)/\1/g' /etc/locale.gen
     # diff -u /etc/locale.gen.bak /etc/locale.gen

  ※ロケールの作成
  # locale-gen

  # echo 'LC_ALL="ja_JP.UTF-8"' > /etc/env.d/02locale
  # echo 'LANG="ja_JP"' >> /etc/env.d/02locale
  # cat /etc/env.d/02locale

TIMEZONEの設定
==============
Japanにする場合 ::

  # ls -l /usr/share/zoneinfo/Japan
  # cp /usr/share/zoneinfo/Japan /etc/localtime
  # echo "Japan" > /etc/timezone
  # cat /etc/timezone

Asia/Tokyoにする場合 ::

  # ls -l /usr/share/zoneinfo/Asia/Tokyo
  # cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
  # echo "Asia/Tokyo" > /etc/timezone
  # cat /etc/timezone

デバイス確認系のツールをインストール
====================================
::

   # emerge -avt sys-apps/ethtool
     ※ ethtoolコマンドの為
   # emerge -avt pciutils
     ※ lspci, lsmodの為
   # emerge -avt sys-apps/lshw
     ※ lshwコマンドの為

   # まとめてインストール
   # emerge -avt sys-apps/ethtool pciutils sys-apps/lshw


