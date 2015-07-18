========================
Gentooのネットワーク設定
========================


ホスト名の設定
==============
::

   # vim /etc/conf.d/hostname

      ※ sphinxの例
      hostname="sphinx"

   # ワンライナーの例
   # echo hostname="sphinx" > /etc/conf.d/hostname

物理インターフェースの確認
==========================
::

   # udevadm test-builtin net_id /sys/class/net/eth0 2> /dev/null
   例: ID_NET_NAME_PATH=enp3s0f0

   # udevadm test-builtin net_id /sys/class/net/eth1 2> /dev/null
   例: ID_NET_NAME_PATH=enp3s0f1

* ブートしたメディアによってインターフェース名がまちまちになる場合があるので念のための確認
* VMの場合 *ID_NET_NAME_MAC=* の値が出る事があるが、これは無視をして eth0,eth1... で良い。

あたりを付けたインターフェースがリンクアップしている事を確認 ::

   # ethtool enp3s0f0
   # ethtool enp3s0f1

   ※ ethtoolパッケージが必要

ネットワーク設定
================
::

   # vim /etc/conf.d/net

シングルインターフェースの設定例 ::

   config_enp0s25="192.168.1.173/24"
   routes_enp0s25="default via 192.168.1.254"
   dns_servers_enp0s25="192.168.1.200"
   dns_domain_enp0s25="otokojuku.local"
   dns_search_enp0s25="otokojuku.local"
   nis_domain_enp0s25="otokojuku.local"
   nis_servers_enp0s25="192.168.1.200"


作成したインターフェースをスタートアップに入れる ::


    ※ インターフェースが enp0s25 の場合は bootのランレベルにnet.enp0s25を追加
    # cd /etc/init.d
    # ln -s net.lo net.enp0s25
    # rc-update add net.enp0s25 boot

    ※ net.eth0 の場合
    # ln -s net.lo net.eth0
    # rc-update add net.eth0 boot

