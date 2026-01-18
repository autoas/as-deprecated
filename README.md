# This repo is no longer active supported, a new project is started and source code opened at
# https://github.com/autoas/as

# as
automotive software and its tool-chain

[![Build Status](https://travis-ci.org/autoas/as.svg?branch=master)](https://travis-ci.org/autoas/as)

## why this repository
Because I am not powerful so I decided to develop tiny but smart part of automotive software based on open source, and create a general AUTOSAR & Automotive Software study environment.

As below picture shows, it was an virtual cluster based on AUTOSAR and can be simulated on Windows and Linux.

![ascore posix vic on AUTOSAR](https://github.com/autoas/as/raw/gh-pages/images/ascore_posix_vic.gif)

## Key Point

### 1. BSW

#### 1.1 Integrated ArcCore AUTOSAR 3.1 BSW
* Communication: Can(CanFD) CanIf PduR Com SoAd J1939Tp
* Diagnostic: CanTp Dcm DoIP Dem
* System: EcuM SchM
* Memory: Fls Fee Eep Ea NvM MemIf

#### 1.2 AS Mini BSW
Mainly for the purpose to create a small footprint bootloader with all of the code implemented by me.

* Diagnostic: [CanTpMini](https://github.com/autoas/as/blob/master/com/as.infrastructure/communication/CanTp/CanTpMini.c) [DcmMini](https://github.com/autoas/as/tree/master/com/as.infrastructure/diagnostic/Dcm/DcmMini.c)



### 2. OS [ASKAR](https://github.com/autoas/as/tree/master/com/as.infrastructure/system/kernel/askar) - [Automotive oSeK AutosaR](http://autoas.github.io/as/autosar/2017/10/27/ASKAR-architecture.html)
This RTOS ASKAR is designed according to [OSEK/VDX OS223](http://trampolinebin.rts-software.org/os223.pdf) by taking a reference of a lot of other open source RTOS, generally, the bwlow is the list:

* [toppers_osek](https://www.toppers.jp/osek-os.html)
* [FreeOSEK](http://opensek.sourceforge.net/)
* [FreeRTOS](http://www.freertos.org/)
* [ucos ii](https://www.micrium.com/)
* [toppers-atk2](https://www.toppers.jp/atk2.html)
* [contiki](http://contiki-os.org/)
* [trampoline](https://github.com/TrampolineRTOS/trampoline)
* [rtthread](https://github.com/RT-Thread/rt-thread)

For the purpose that to be able to run most of the common applications which are based on posix, a series of posix APIs have been implemented based on the ASKAR OSEK tiny core.

* posix threads
* posix semaphore
* posix mutex and condition
* posix message queue
* posix signals

General supported CPU architecture list:

* arm32: cortex-m3 arm926
* arm64: cortex-a57 (multicore is supported)
* ppc: mpc5634
* intel: i386
* s12cpuv2: mc9s12xep100


## 3. BSW configuration tool
> This GUI tool is the one from [OpenSAR](https://github.com/parai/OpenSAR.git) which is also developed by me, the GUI can be automatically created from xml.

![as configure tool](http://autoas.github.io/as/images/config.infrastructure.system.gif)

## 4. AUTOSAR & LINUX communication
* [virtio](http://docs.oasis-open.org/virtio/virtio/v1.0/csprd01/virtio-v1.0-csprd01.pdf)
* [remoteproc](https://www.kernel.org/doc/Documentation/remoteproc.txt)
* [rpmsg](https://www.kernel.org/doc/Documentation/rpmsg.txt)
* [virtio ring buffer](http://www.ibm.com/developerworks/cn/linux/1402_caobb_virtio/)

## 5. Lua & Python Integrated
* support CAN device by lascanlib or pyas: CANcaseXL, [PeakCAN](http://www.peak-system.com/PCAN-USB.199.0.html?L=1), [SocketCAN](https://en.wikipedia.org/wiki/SocketCAN), [ZLG USBCAN](http://www.zlg.cn/can/can/product/id/22.html)
* support miscellaneous device by lasdevlib with the smae API interface "open/read/write/ioctl/close": rs232
* a powerful python as.one.py tool: Dcm Xcp Bootloader and others.
* a powerful third party RTE tool integrated: [cogu/autosar](https://github.com/cogu/autosar)

![as.one.py bootloader](http://autoas.github.io/as/images/python3-asone-tool.png)

## 6. Other 3rd part package
* [LWIP](http://savannah.nongnu.org/projects/lwip/): about text:133Kb, data:11Kb
* [contiki-net](http://contiki-os.org/): about text:54Kb(including the protothread), data:4Kb
* [afbinder/websock](https://github.com/automotive-grade-linux/docs-agl/blob/master/docs/app-framework/index.md)
* qemu PCI sample driver: [asnet](https://github.com/autoas/as/blob/master/com/as.tool/qemu/hw/char/asnet.c) [ascan](https://github.com/autoas/as/blob/master/com/as.tool/qemu/hw/char/ascan.c) [asblk](https://github.com/autoas/as/blob/master/com/as.tool/qemu/hw/char/asblk.c)
* [FatFS](http://elm-chan.org/fsw/ff/00index_e.html)
* [lwext4](https://github.com/gkostka/lwext4.git)
* libelf: an OS independent ELF library for ELF loading&executing.
* [LVGL](https://github.com/littlevgl/lvgl):Littlev Graphics Libraray
* [DTC/LIBFDT](https://github.com/dgibson/dtc) 

## 7. Setup Environment and Run

>Check the page [as-study-platform](http://autoas.github.io/as/autosar/2018/02/20/as-study-platform.html) for how to setup the environment from zero by yourself.

## 8. AS USB2CAN device

[stm32f107vc USB2CAN](https://github.com/as-boards/stm32f107vc)

![stm32](https://github.com/as-boards/stm32f107vc/blob/master/doc/usb2can_dut_demo.jpg)

