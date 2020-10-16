# Infinity R1

A brave effort to make a flashable linux image for the InfinityR1 (8G1/512M) AI Soundbox

:warning: WARNING :warning:
```
 Experimental stuff going on here, proceed with caution! 
```


InfinityR1 8G/512M


- CPU : Rockchip RK3229 quad core ARM Cortex A7 processor @1.5 GHz
- GPU : ARM Mali-400MP
- Memory : 512M DDR3
- Storage : 8GB samsung emmc flash,KLM8G1GEME-B041 8GB 16nm，EMMC5.1
#- Video Output : HDMI 2.0 up to 4K2K @60 fps, and 3.5mm AV output (composite)
- Audio Input ： 
  - 4x MIC
  - 3x ES7243 ADC IIS/ADC
- Audio Output : DAC stereo|Mono ADC AK7755 to AMP TI TPA3118 class D
#HDMI, AV, and coaxial S/PDIF
- Connectivity : wifi and bluetooth,CYPRESS CYW43455/802.11n/ac,BT4.2
#100Mbps Ethernet, 802.11 b/g/n WiFi
- USB : 1x USB 2.0 host ports|OTG
- Interfaces : 1x USB
#HDMI port, RJ45 port, SPDIF port, 4x USB Host, SD Card Slot, AV Out DC jack.
- Power Supply : 5V/2A

## TODO
- [x] get UART output through USB OTG
- [ ] Build own U-Boot / Kernel / rootfs
- [ ] Video Output while booting
- [ ] Enable UART routing to USB port(?)
- [ ] Enable netbooting

# How-to UART

###### What you need
- Patch a micro usb connector or wired directly.
- an USB-TTL adaptor such as CH340.


###### Wiring
the Check point on board and connect way as below.
```

```

USB-TTL to UART wiring

```
USB-TTL     UART
  OTG/ID -> TP12(not connected)
  RXD   ->   TP13/DP 
  TXD   ->   TP14/DM
  GND   ->   GND
```
Connect USB-TTL and open terminal emulator of choice
```
Baudraute : 1.5M(1500000)
Data bits : 8M
Stop bits : 1
```
Important:  need connect r211 with the GND and plugin the power supply to soundbox.

# How-to Build U-Boot

Follow this guide

or..

One [script](scripts/README.md) to handle it all



## How to flash new u-boot.img to board



## How-To boot the new u-boot.img from SD

# How to..

## How-to recover

- Start AndroidTool/RKBatchTool
- Shorten pins 8 & 9 on the nand chip (see image and make sure you do this right!!!)
- Power up using the OTG port

You should now see 'Found One MASKROM Device'

- Click the 'Upgrade Firmware' tab, then 'EraseFlash' (i had to select firmware before erasing)
- If successful, hit the 'Upgrade' button

All good?

## Repair corrupted SDcard..
Red LED after tampering with the files on SDcard? 
```
sudo fdisk -l
sudo fsck -a /dev/sd[partition] 
```
###### 
