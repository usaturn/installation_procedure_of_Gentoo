===============
make.confの設定
===============

* コンパイルオプションの設定
* ミラーサイトの選択

エディタで編集をする ::

   # vim /mnt/gentoo/etc/portage/make.conf

お好みで ::

      # 物理マシンの場合は -march=native
      # 仮想マシンは -march=x86-64
      CFLAGS="-march=native -O2"
      # 両方の変数に同じ値を使います
      CXXFLAGS="${CFLAGS}"
      # コア数 + 1 程度
      MAKEOPTS="-j12"
      # USEフラグ
      USE="mmx sse sse2 cjk unicode nptl nptlonly threads nls"
      USE="${USE} acpi dbus hal xml pam nis nfs"
      USE="${USE} -alsa -cups -gnome -gtk -ipv6 -kde -nls -oss -perl -qt3 -qt4 -ruby -X"

      LINGUAS="ja"
      GENTOO_MIRRORS="ftp://ftp.iij.ad.jp/pub/linux/gentoo/ ftp://ftp.jaist.ac.jp/pub/Linux/Gentoo/"

      # portage log
      PORT_LOGDIR="/var/log/portage"
      PORTAGE_ELOG_CLASSES="warn error log"
      PORTAGE_ELOG_SYSTEM="save"

      PYTHON_TARGETS="python2_7"


