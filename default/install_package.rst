==================================
必要なパッケージをインストールする
==================================
NICのbondingをしている場合は ``ifenslave`` が必要 ::

  # emerge -avt net-misc/ifenslave
  ※ bondingをしない、あるいはbond0を作成していない場合は不要

ファイルシステムをreiserfsにしている場合は専用パッケージが必要 ::

   # emerge -avt sys-fs/reiserfsprogs

シスログツール ::

   ※ syslog-ng
   # emerge -avt syslog-ng
   # rc-update add syslog-ng default

   ※ rsyslogを入れる場合
   # emerge -avt rsyslog
   # rc-update add rsyslog default

cron ::

   # emerge -avt vixie-cron
   # rc-update add vixie-cron default

マイクロコードのアップデート ::

   # emerge -avt sys-kernel/linux-firmware
   ※ 入れておいた方が無難。サーバ製品でbroadcomのNICが使えるようになった例あり


