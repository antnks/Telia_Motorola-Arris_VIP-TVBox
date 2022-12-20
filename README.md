# Telia_Motorola-Arris_VIP-TVBox

### Above -> (SDCARD = Slot 2, used for firmware downgrade/upgrade)

![Screenshot_20221220_041738](https://user-images.githubusercontent.com/26827453/208573712-b0bd62f8-e666-4a31-9542-6ad187acf18b.png)

### Under 

![20221220_012440](https://user-images.githubusercontent.com/26827453/208572105-37c56c69-0eb0-48ff-954c-c96886727533.jpg)

### Soldering Pins 

![Screenshot_20221220_040648](https://user-images.githubusercontent.com/26827453/208572585-30da72b9-ecfd-4dbf-81be-6e6baa934a16.png)



### General Info

```
User-Agent (OLD).....................: KreaTVWebKit/531 (Motorola STB; Linux)
User-Agent...........................: KreaTVWebKit/600 (Motorola STB; Linux; 5305)

Default login URL....................: http://iptvlogin.telia.se/credentials
Login URL for Device Codes...........: http://iptvlogin.telia.se/iptvgui/guiV8_13_03_433d01a514_swe
Login Referer URL....................: telia.api-test.ruwido.com
Login Test API.......................: https://telia.api-test.ruwido.com/rc_config/c7f585f72324/v2/meta/EDID/signal?output=base64_blob
Teliasonera rootcva1.................: http://crl-3.trust.teliasonera.com/teliasonerarootcav1.crl
Teliasonera Repository Trust CPS.....: http://repository.trust.teliasonera.com/CPS
Telia OCSP Trust URL.................: http://ocsp.trust.telia.com
Telia OCSP Trust CSP Download........: https://repository.trust.teliasonera.com/CPS
TeliaSonera root cav1.cer cert.......: http://repository.trust.teliasonera.com/teliasonerarootcav1.cer
TeliaSonera Server cav2.cer file.....: http://repository.trust.teliasonera.com/teliasoneraservercav2.cer
```

### Download and Backup your splash theme if you want to replace the splash theme during boot

Kernel Version Example: `kreatelVhi53_5_5_1_p4_220425_SWE_13852`

```
http://image.iptv.telia.se/teliasonera-vip5305?product=teliasonera-vip5305&serial=<TV_BOX_SERIAL>&mac=<TV_BVOX_MAC_ADDRESS_HERE>&fw_version=7.12.2&kernel_version=<CURRENT_KERNEL_VERSION_HERE>&splash_version=5305_1
```

### Download default splash theme used from stock rom

```bash
wget2 –user-agent="KreaTVWebKit/600 (Motorola STB; Linux; 5305)" \
  https://wpc.97697.teliacdn.net/8097697/ott/splashTheme.pkg.sec
```

### Get http.requests uri (execute on router for virtual iptv interface)

```bash
tshark -i vlan_iptv -T fields -e http.request.uri |grep \S
```

#### Available urls

```bash
/iptvgui/ikons_1920x1080/channelIcon_0.png
/iptvgui/ikons_1920x1080/channelIcon_430.png
/iptvgui/ikons_1920x1080/channelIcon_438.png
/iptvgui/ikons_1920x1080/channelIcon_440.png
/iptvgui/ikons_1920x1080/channelIcon_444.png
/iptvgui/ikons_1920x1080/channelIcon_100.png
/iptvgui/ikons_1920x1080/channelIcon_109.png
/iptvgui/ikons_1920x1080/channelIcon_435.png
/iptvgui/ikons_1920x1080/channelIcon_463.png
/iptvgui/ikons_1920x1080/channelIcon_491.png
/iptvgui/ikons_1920x1080/channelIcon_462.png
/iptvgui/ikons_1920x1080/channelIcon_437.png
/iptvgui/ikons_1920x1080/channelIcon_471.png
/iptvgui/ikons_1920x1080/channelIcon_470.png
/iptvgui/ikons_1920x1080/channelIcon_472.png
/iptvgui/ikons_1920x1080/channelIcon_26.png
/iptvgui/ikons_1920x1080/channelIcon_445.png
/iptvgui/ikons_1920x1080/channelIcon_67.png
/iptvgui/ikons_1920x1080/channelIcon_58.png
/iptvgui/ikons_1920x1080/channelIcon_270.png
/iptvgui/ikons_1920x1080/channelIcon_777.png
/iptvgui/ikons_1920x1080/channelIcon_3063.png
/iptvgui/ikons_1920x1080/channelIcon_3064.png
/iptvgui/ikons_1920x1080/channelIcon_522.png
and alot more....
```

### Download all tv icons available from Telia:

* Also available in icon folder in this repository

```bash
for icons in $(seq 0 1000); do 
  wget2 –user-agent="KreaTVWebKit/600 (Motorola STB; Linux; 5305)" \
    http://iptv-icons.telia.se/iptvgui/ikons_1920x1080/channelIcon_${icons}.png; 
done
```


We don't get any shell via serial via UART, this is all we gonna see from bootlog

## Bootlog

```
System memory: 2048 MB

Using Slot 1
Using two stage boot
Unpacking Image ...Done
hisilicon-pcie f0001000.pcie: missing *config* reg space
hisilicon-pcie f0001000.pcie: PCIe Link Fail
pcieport 0000:00:00.0: buffer not found in pci_save_pcie_state
starting pid 147, tty '/dev/console': '/etc/rc.sysinit'
mount: mounting none on /var/extstorage failed: No such file or directory
fb_mem=250000
insmod hi_fb.ko video="hifb:vram0_size:250000"
insmod hi_ir.ko key_fetch=1
date: can't set date: Invalid argument
Thu Jan  1 00:00:00 UTC 1970
Note: Already updated, signature is the same
/etc/rc.sysinit: line 282: can't create /proc/sys/net/ipv4/conf/eth1/force_igmp_version: nonexistent directory
chmod: /usr/bin/logapp.sh: Read-only file system
Error: Unable to read name service address from file /tmp/nameservice_address defined by NS_ADDRESS_FILENAME
```

## Reboot

```
reboot: Restarting system

System memory: 2048 MB

Using Slot 1
Using two stage boot
Unpacking Image ...Done
hisilicon-pcie f0001000.pcie: missing *config* reg space
hisilicon-pcie f0001000.pcie: PCIe Link Fail
pcieport 0000:00:00.0: buffer not found in pci_save_pcie_state
starting pid 147, tty '/dev/console': '/etc/rc.sysinit'
mount: mounting none on /var/extstorage failed: No such file or directory
fb_mem=250000
insmod hi_fb.ko video="hifb:vram0_size:250000"
insmod hi_ir.ko key_fetch=1
date: can't set date: Invalid argument
Thu Jan  1 00:00:00 UTC 1970
Note: Already updated, signature is the same
/etc/rc.sysinit: line 282: can't create /proc/sys/net/ipv4/conf/eth1/force_igmp_version: nonexistent directory
chmod: /usr/bin/logapp.sh: Read-only file system
Error: Unable to read name service address from file /tmp/nameservice_address defined by NS_ADDRESS_FILENAME
⸮^@^@^@
```

### Firmware

I found the source for Arris firmware, it can be found on url below (i created this script for find the firmwares)

```bash
#!/usr/bin/env bash

# - iNFO ----------------------------------------------------------------------------
#
#        Author: wuseman <wuseman@nr1.nu>
#      FileName: wtelia-tv-spider.sh
#       Version: 1.0
#
#       Created: 2022-12-20 (02:03:48)
#      Modified: 2022-12-20 (02:09:54)
#
#           iRC: wuseman (Libera/EFnet/LinkNet)
#      Telegram: https://t.me/wuseman
#
#          Blog: https://wuseman.se
#       Website: https://www.nr1.nu/
#        GitHub: https://github.com/wuseman/
#
# - LiCENSE ------------------------------------------------------------------------
source="http://wpc.97697.teliacdn.net/8097697/ott/stbimage"

if [[ ! -f "~/telia-tv-firmware.log" ]]; then 
  touch ~/telia-tv-firmware.log; fi

wget2 &> /dev/null;[[ $? -ne "0" ]] && printf '%s\n' 'wget2 is reuqired ot be installed'; exit 

for version in $(seq -w 0000 9999); do
        wget2 --spider –user-agent="KreaTVWebKit/600 (Motorola STB; Linux; 5305)" \
        ${source}-${version}Swe|grep -iq "OK"
        if [[ $? = "0" ]]; then
                echo -e "[\e[1;32m+\e[0m] - Firmware found: ${source}-${version}Swe" \
                echo -e "${source}-${version}Swe" >>  ~/telia-tv-firmware.log
                                else
                echo -e "[\e[1;31m-\e[0m] - Firmware not found: ${source}-${version}Swe"
        fi
done
```

* [Firmware 4302Swe](http://wpc.97697.teliacdn.net/8097697/ott/stbimage-4302Swe)
* [Firmware 5305Swe](http://wpc.97697.teliacdn.net/8097697/ott/stbimage-5305Swe)

### Download currnet kernel (mask this part so we wont show who we are)

Edit: 

* mac_addr
* serial
* kernel

```bash
curl 'https://image.iptv.telia.se/teliasonera-vip5305?product=teliasonera-vip5305&serial=<serial>&mac=<mac_addr>&fw_version=7.12.2&kernel_version=<kernel>&splash_version=5305_1%20HTTP/1.1' \
  -H 'Upgrade-Insecure-Requests: 1' \
  -H 'User-Agent: KreaTVWebKit/600 (Motorola STB; Linux; 5305)' \
  -H 'sec-ch-ua-platform: "TV Box"' \
  --compressed
```

Output: 

```
<?xml version="1.0"?>
<!DOCTYPE StbConfig SYSTEM "stbconfig.dtd">
<StbConfig><BootParams>
  <KernelUrl>http://wpc.97697.teliacdn.net:80/8097697/ott/stbimage-5305Swe</KernelUrl>
  <KernelVersion>kreatelVhi53_5_5_1_p6_220519_SWE_13956</KernelVersion><ThemeUrl>http://wpc.97697.teliacdn.net:80/8097697/ott/splashimageSweTheme.pkg.sec</ThemeUrl>
<ThemeVersion>1.2</ThemeVersion>
</BootParams>
</StbConfig>
```
