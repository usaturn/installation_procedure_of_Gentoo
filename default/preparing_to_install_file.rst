==========================
インストール用ファイル準備
==========================

作業領域にカレントを移し、stage3のアーカイブをダウンロード、展開する ::

   # cd /mnt/gentoo
   # wget http://ftp.iij.ad.jp/pub/linux/gentoo/releases/amd64/autobuilds/current-stage3-amd64/stage3-amd64-20150709.tar.bz2.DIGESTS
   # wget http://ftp.iij.ad.jp/pub/linux/gentoo/releases/amd64/autobuilds/current-stage3-amd64/stage3-amd64-20150709.tar.bz2
     ※ あらかじめ http://ftp.iij.ad.jp/pub/linux/gentoo/releases/amd64/autobuilds/current-stage3-amd64/ をローカル端末のブラウザで確認する
     ※ 最新の日付の stage3-*.tar.bz2 のURLをwgetの引数にする
     ※ 最新の日付の stage3-*.tar.bz2.DIGESTS のURLをwgetの引数にする
   # sha512sum -c *.DIGESTS
   # tar xf stage3-*.tar.bz2

Portageスナップショットをダウンロードし、インストール

※後でemerge-webrsyncを使う場合は不要。確実にダウンロードしたい時に実施。

::

   # cd /mnt/gentoo
   # wget http://ftp.iij.ad.jp/pub/linux/gentoo/releases/snapshots/current/portage-latest.tar.bz2.md5sum
   # wget http://ftp.iij.ad.jp/pub/linux/gentoo/releases/snapshots/current/portage-latest.tar.bz2
   # md5sum -c portage-latest.tar.bz2.md5sum
   # tar xf /mnt/gentoo/portage-latest.tar.bz2 -C /mnt/gentoo/usr

