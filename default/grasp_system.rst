========================
システムの情報を把握する
========================


あとで実施するカーネル設定のデバイスドライバなどの参考にlspciの結果をメモっておく

DELLサーバ例::

   # lspci

   00:00.0 Host bridge: Intel Corporation 5500 I/O Hub to ESI Port (rev 13)
   00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
   00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
   00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
   00:09.0 PCI bridge: Intel Corporation 7500/5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
   00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13)
   00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
   00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
   00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
   00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
   00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
   00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
   00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
   00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
   00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
   00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
   00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
   00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA Controller [IDE mode] (rev 02)
   01:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
   01:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
   02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
   02:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
   03:00.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 1078 (rev 04)
   06:03.0 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200eW WPCM450 (rev 0a)
   fe:00.0 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture Generic Non-core Registers (rev 02)
   fe:00.1 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture System Address Decoder (rev 02)
   fe:02.0 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 0 (rev 02)
   fe:02.1 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 0 (rev 02)
   fe:02.2 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 0 (rev 02)
   fe:02.3 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 1 (rev 02)
   fe:02.4 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 1 (rev 02)
   fe:02.5 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 1 (rev 02)
   fe:03.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Registers (rev 02)
   fe:03.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Target Address Decoder (rev 02)
   fe:03.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller RAS Registers (rev 02)
   fe:03.4 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Test Registers (rev 02)
   fe:04.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Control (rev 02)
   fe:04.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Address (rev 02)
   fe:04.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Rank (rev 02)
   fe:04.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Thermal Control (rev 02)
   fe:05.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Control (rev 02)
   fe:05.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Address (rev 02)
   fe:05.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Rank (rev 02)
   fe:05.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Thermal Control (rev 02)
   fe:06.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Control (rev 02)
   fe:06.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Address (rev 02)
   fe:06.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Rank (rev 02)
   fe:06.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Thermal Control (rev 02)
   ff:00.0 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture Generic Non-core Registers (rev 02)
   ff:00.1 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture System Address Decoder (rev 02)
   ff:02.0 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 0 (rev 02)
   ff:02.1 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 0 (rev 02)
   ff:02.2 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 0 (rev 02)
   ff:02.3 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 1 (rev 02)
   ff:02.4 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 1 (rev 02)
   ff:02.5 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 1 (rev 02)
   ff:03.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Registers (rev 02)
   ff:03.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Target Address Decoder (rev 02)
   ff:03.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller RAS Registers (rev 02)
   ff:03.4 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Test Registers (rev 02)
   ff:04.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Control (rev 02)
   ff:04.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Address (rev 02)
   ff:04.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Rank (rev 02)
   ff:04.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Thermal Control (rev 02)
   ff:05.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Control (rev 02)
   ff:05.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Address (rev 02)
   ff:05.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Rank (rev 02)
   ff:05.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Thermal Control (rev 02)
   ff:06.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Control (rev 02)
   ff:06.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Address (rev 02)
   ff:06.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Rank (rev 02)
   ff:06.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Thermal Control (rev 02)

   # lsmod

   Module                  Size  Used by
   video                  16669  0
   shpchp                 29606  0
   iTCO_wdt               16534  0
   joydev                 16536  0
   coretemp               12441  0
   iTCO_vendor_support    12640  1 iTCO_wdt
   acpi_power_meter       16564  0
   i7core_edac            20630  0
   dcdbas                 12434  0
   crc32c_intel           12441  0
   ghash_clmulni_intel    12567  0
   serio_raw              12440  0
   microcode              20803  0
   edac_core              31525  4 i7core_edac
   raid10                 32930  0
   raid456                53468  0
   async_raid6_recov      12506  1 raid456
   async_pq               12535  2 raid456,async_raid6_recov
   raid6_pq               82623  2 async_pq,async_raid6_recov
   async_xor              12453  3 async_pq,raid456,async_raid6_recov
   xor                    12426  1 async_xor
   async_memcpy           12389  2 raid456,async_raid6_recov
   async_tx               12625  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
   raid1                  28847  0
   raid0                  16516  0
   multipath              12391  0
   linear                 12391  0
   ses                    12391  0
   enclosure              12743  1 ses
   usb_storage            46994  1
   megaraid_sas           64217  2
   bnx2                   61718  0

仮想マシンの例 ::

   # lspci

   00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
   00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
   00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
   00:01.2 USB controller: Intel Corporation 82371SB PIIX3 USB [Natoma/Triton II] (rev 01)
   00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
   00:02.0 VGA compatible controller: Cirrus Logic GD 5446
   00:03.0 Ethernet controller: Red Hat, Inc Virtio network device
   00:04.0 SCSI storage controller: Red Hat, Inc Virtio block device
   00:05.0 Unclassified device [00ff]: Red Hat, Inc Virtio memory balloon

   # lsmod

   Module                  Size  Used by
   video                  16669  0
   microcode              20803  0
   virtio_balloon         12470  0
   i2c_piix4              12438  0
   i2c_core               22165  1 i2c_piix4
   raid10                 32930  0
   raid456                53468  0
   async_raid6_recov      12506  1 raid456
   async_pq               12535  2 raid456,async_raid6_recov
   raid6_pq               82623  2 async_pq,async_raid6_recov
   async_xor              12453  3 async_pq,raid456,async_raid6_recov
   xor                    12426  1 async_xor
   async_memcpy           12389  2 raid456,async_raid6_recov
   async_tx               12625  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
   raid1                  28847  0
   raid0                  16516  0
   multipath              12391  0
   linear                 12391  0
   virtio_blk             12574  3
   virtio_net             16624  0

   # SystemRescueCdから実行
   # lshw

   sysresccd
       description: Computer
       product: Bochs ()
       vendor: Bochs
       width: 64 bits
       capabilities: smbios-2.4 dmi-2.4 vsyscall32
       configuration: boot=normal uuid=A6D94863-A56B-429F-8FE6-164D39E8A3E4
     *-core
          description: Motherboard
          physical id: 0
        *-firmware
             description: BIOS
             vendor: Bochs
             physical id: 0
             version: Bochs
             date: 01/01/2011
             size: 96KiB
        *-cpu:0
             description: CPU
             product: Westmere E56xx/L56xx/X56xx (Nehalem-C)
             vendor: Intel Corp.
             physical id: 401
             bus info: cpu@0
             slot: CPU 1
             size: 2GHz
             capacity: 2GHz
             width: 64 bits
             capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx rdtscp x86-64 constant_tsc arch_perfmon rep_good nopl pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 popcnt aes hypervisor lahf_lm
        *-cpu:1
             description: CPU
             product: Westmere E56xx/L56xx/X56xx (Nehalem-C)
             vendor: Intel Corp.
             physical id: 402
             bus info: cpu@1
             slot: CPU 2
             size: 2GHz
             capacity: 2GHz
             width: 64 bits
             capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx rdtscp x86-64 constant_tsc arch_perfmon rep_good nopl pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 popcnt aes hypervisor lahf_lm
        *-cpu:2
             description: CPU
             product: Westmere E56xx/L56xx/X56xx (Nehalem-C)
             vendor: Intel Corp.
             physical id: 403
             bus info: cpu@2
             slot: CPU 3
             size: 2GHz
             capacity: 2GHz
             width: 64 bits
             capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx rdtscp x86-64 constant_tsc arch_perfmon rep_good nopl pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 popcnt aes hypervisor lahf_lm
        *-cpu:3
             description: CPU
             product: Westmere E56xx/L56xx/X56xx (Nehalem-C)
             vendor: Intel Corp.
             physical id: 404
             bus info: cpu@3
             slot: CPU 4
             size: 2GHz
             capacity: 2GHz
             width: 64 bits
             capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx rdtscp x86-64 constant_tsc arch_perfmon rep_good nopl pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 popcnt aes hypervisor lahf_lm
        *-memory
             description: System Memory
             physical id: 1000
             size: 2GiB
             capacity: 2GiB
           *-bank
                description: DIMM RAM
                physical id: 0
                slot: DIMM 0
                size: 2GiB
                width: 64 bits
        *-pci
             description: Host bridge
             product: 440FX - 82441FX PMC [Natoma]
             vendor: Intel Corporation
             physical id: 100
             bus info: pci@0000:00:00.0
             version: 02
             width: 32 bits
             clock: 33MHz
           *-isa
                description: ISA bridge
                product: 82371SB PIIX3 ISA [Natoma/Triton II]
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:00:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: isa
                configuration: latency=0
           *-ide
                description: IDE interface
                product: 82371SB PIIX3 IDE [Natoma/Triton II]
                vendor: Intel Corporation
                physical id: 1.1
                bus info: pci@0000:00:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master
                configuration: driver=ata_piix latency=0
                resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:c0a0(size=16)
           *-usb
                description: USB controller
                product: 82371SB PIIX3 USB [Natoma/Triton II]
                vendor: Intel Corporation
                physical id: 1.2
                bus info: pci@0000:00:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: uhci bus_master
                configuration: driver=uhci_hcd latency=0
                resources: irq:11 ioport:c040(size=32)
           *-bridge
                description: Bridge
                product: 82371AB/EB/MB PIIX4 ACPI
                vendor: Intel Corporation
                physical id: 1.3
                bus info: pci@0000:00:01.3
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bridge
                configuration: driver=piix4_smbus latency=0
                resources: irq:9
           *-display
                description: VGA compatible controller
                product: GD 5446
                vendor: Cirrus Logic
                physical id: 2
                bus info: pci@0000:00:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller rom
                configuration: driver=cirrus latency=0
                resources: irq:0 memory:fc000000-fdffffff memory:febf0000-febf0fff memory:febe0000-febeffff
           *-network
                description: Ethernet interface
                product: Virtio network device
                vendor: Red Hat, Inc
                physical id: 3
                bus info: pci@0000:00:03.0
                logical name: eth0
                version: 00
                serial: 52:54:00:4d:8e:91
                width: 32 bits
                clock: 33MHz
                capabilities: msix bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=virtio_net driverversion=1.0.0 ip=192.168.1.175 latency=0 link=yes multicast=yes
                resources: irq:10 ioport:c060(size=32) memory:febf1000-febf1fff memory:febc0000-febdffff
           *-scsi
                description: SCSI storage controller
                product: Virtio block device
                vendor: Red Hat, Inc
                physical id: 4
                bus info: pci@0000:00:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: scsi msix bus_master cap_list
                configuration: driver=virtio-pci latency=0
                resources: irq:11 ioport:c000(size=64) memory:febf2000-febf2fff
           *-generic
                description: Unclassified device
                product: Virtio memory balloon
                vendor: Red Hat, Inc
                physical id: 5
                bus info: pci@0000:00:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=virtio-pci latency=0
                resources: irq:10 ioport:c080(size=32)
        *-scsi
             physical id: 1
             logical name: scsi1
             capabilities: emulated
           *-cdrom
                description: DVD reader
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /livemnt/boot
                capabilities: audio dvd
                configuration: mount.fstype=iso9660 mount.options=ro,relatime,mode=0644 state=mounted status=ready
   (chroot) sysresccd / #


