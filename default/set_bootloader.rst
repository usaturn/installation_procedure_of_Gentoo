==================
ブートローダの設定
==================

grubのインストール ::

   # emerge -avt sys-boot/grub

grubのセットアップ ::

    # ls -l /etc/grub.d
    # chmod -x /etc/grub.d/{20_linux_xen,30_os-prober,40_custom,41_custom}
    # ls -l /etc/grub.d
    # mkdir -p /boot/grub
    # grub2-mkconfig -o /boot/grub/grub.cfg

          # 正常な出力結果
          Generating grub.cfg ...
          Found linux image: /boot/vmlinuz-3.14.14-gentoo
          Found linux image: /boot/vmlinuz-3.14.14-gentoo.old
          done

    # cat /boot/grub/grub.cfg

シリアルコンソールを設定する場合(仮想マシン向け) ::

    # vim /etc/default/grub
        GRUB_CMDLINE_LINUX="console=ttyS0,115200n8r"
        GRUB_TERMINAL=serial
        GRUB_SERIAL_COMMAND="serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1"

    # grub2-mkconfig -o /boot/grub/grub.cfg
    # cat /boot/grub/grub.cfg

MBRにgrubをインストールする ::

    ※ 物理マシン(適宜)
    # grub2-install /dev/sda

    ※ 仮想マシン(適宜)
    # grub2-install /dev/vda

    ※ 実行後表示例
    (chroot) sysresccd / # grub2-install /dev/vda
    Installation finished. No error reported.

