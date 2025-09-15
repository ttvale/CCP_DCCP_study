# Jakub Klinkovský's configuration files

These are my config files of OpenWrt - an operating system I use in my Ubiquiti RouterStation Pro.


## Installation

    git clone git://github.com/lahwaacz/openwrt-dotfiles.git
    cd openwrt-dotfiles

And now copy the files anywhere you want.


## Environment

### Software

I build the system from trunk source. To get it do the following:

    git clone git://nbd.name/openwrt.git ~/trunk/
    cd ~/trunk

To build it you need to have installed gcc, binutils, patch, bzip2, flex, make, gettext, pkg-config,
unzip, libz-dev and libc headers. Then run `make menuconfig` to configure your firmware and `make`
to build it.


### Hardware

I have a Ubiquiti RouterStation Pro board, these config files may not work on other devices. Especially
`.config` will work only on RouterStation Pro! Also note that RouterStation and RouterStation Pro
are incompatible.

#### Hardware specification

1.  Overall System Configuration

    - CPU Atheros AR7161 MIPS 24Kc running @ 680MHz
    - MEMORY DDR 128MB
    - FLASH SPI 16MB
    - 4-Port Gigabit Ethernet Switch
    - Three MINI-PCI Slots supports Type IIIA
    - USB 2.0 Host
    - Built in RS232/dB9 Connector
    - SDIO
    - On board Real Time Clock "RTC"
    - DC Power Jack
    - 802.3af 48V compatible

2.  Power Supply Range 40VDC to 56VDC

    - Using Higher voltage is recommended since it will use lower current
    - Typical Power Consumption is 3W idle no radios present
    - 5W idle One Radio present
    - 7W while passing 1000Mbps traffic
    - Single RJ45 "J1" is for WAN and 802.3af compatible Power Over Ethernet
    - Supports high power POE up to 25W

3.  Ethernet Interface

    - J1 Single WAN port 10/100/1000
    - J2 Tripple LAN Port 10/100/1000
    - 2 RGMII Ethernet Logical Ports to Ethernet Phy Switch
        - 1 RGMII port for WAN Port
        - 1 RGMII port for LAN Ports
    - Ethernet Phy switch, Atheros AR8316

4.  Real Time Clock "RTC" Interface

    - RTC Interface shares the SPI bus with the on board FLASH
    - Active high signal on SPI CS enables RTC, active low signal on SPI CS enables FLASH
    - Manufacture Part# PCF2123TS [Download Datasheet](http://www.nxp.com/acrobat_download/datasheets/PCF2123_1.pdf)

5.  Supported IO

    ##### UART J3 6 pin Header
    Terminal Settings 
    115200 baud, 8 bits, nor parity, 1 stop bit.
    <table border="1" cellpadding="5">
    <tr>
        <td>Pin Out</td>
        <td></td>
    </tr>
    <tr>
        <td>Pin1</td>
        <td>3.3VDC</td>
    </tr>
    <tr>
        <td>Pin2</td>
        <td>S_in</td>
    </tr>
    <tr>
        <td>Pin3</td>
        <td>NC</td>
    </tr>
    <tr>
        <td>Pin4</td>
        <td>NC</td>
    </tr>
    <tr>
        <td>Pin5</td>
        <td>S_out</td></tr>
    <tr>
        <td>Pin6</td>
        <td>GND</td>
    </tr>
    </table>
    
    ##### JTAG Port "J4"
    14 Pin header
    <table border="1" cellpadding="5">
    <tr>
        <td>Pin Out</td>
        <td></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
         <td>Pin1</td>
         <td>TRST</td>
         <td>Pin2</td>
         <td>GND</td>
    </tr>
    <tr>
         <td>Pin3</td>
         <td>TDI</td>
         <td>Pin4</td>
         <td>GND</td>
    </tr>
    <tr>
        <td>Pin5</td>
        <td>TDO</td>
        <td>Pin6</td>
        <td>GND</td>
    </tr>
    <tr>
        <td>Pin7</td>
        <td>TMS</td>
        <td>Pin8</td>
        <td>GND</td>
    </tr>
    <tr>
        <td>Pin9</td>
        <td>TCK</td>
        <td>Pin10</td>
        <td>GND</td>
    </tr>
    <tr>
        <td>Pin11</td>
        <td>RST</td>
        <td>Pin12</td>
        <td>NC</td>
    </tr>
    <tr>
        <td>Pin13</td>
        <td>NC</td>
        <td>Pin14</td>
        <td>3.3VDC</td>
    </tr>
    </table>
    
    ##### USER GPIO Header "J33"
    Single Row 7 Pin Header Also next to it J5 dual row header to enable pull-up or pull-down for each GPIO user selectable in case User needs Active Low or Active High GPIO
    J33 Pin out and Strapping option "place shunt to enable strapping option"
    <table border="1" cellpadding="5">
    <tr>
        <td>Pin Out</td>
        <td>NAME</td>
        <td>J5 STRAPPING</td>
    </tr>
    <tr>
        <td>Pin1</td>
        <td>GPIO_0</td>
        <td>PULL LOW</td>
    </tr>
    <tr>
        <td>Pin2</td>
        <td>GPIO_1</td>
        <td>PULL LOW</td>
    </tr>
    <tr>
        <td>Pin3</td>
        <td>GPIO_3</td>
        <td>PULL LOW</td>
    </tr>
    <tr>
        <td>Pin4</td>
        <td>GPIO_4</td>
        <td>PULL LOW</td>
    </tr>
    <tr>
        <td>Pin5</td>
        <td>GPIO_5</td>
        <td>PULL HIGH</td>
    </tr>
    <tr>
        <td>Pin6</td>
        <td>GPIO_6</td>
        <td>PULL HIGH</td>
    </tr>
    <tr>
        <td>Pin7</td>
        <td>GPIO_7</td>
        <td>PULL HIGH</td>
    </tr>
    </table>
    
    ##### RESET BUTTON "SW4"
    Uses GPIO_8 with weak pull-up, Active Low, for Resting back to factory defaults or multiple functions software dependent.
    
    ##### LED INDICATORS
    Link/Act signals are connected to the Ethernet Phy Switch
    <table border="1" cellpadding="5">
    <tr>
        <td>LED</td>
        <td>NAME</td>
        <td>FUNCTION</td>
        <td>GPIO</td>
    </tr>
    <tr>
        <td>D29</td>
        <td>POWER</td>
        <td>3.3VDC</td>
        <td>NA</td>
    </tr>
    <tr>
        <td>D24</td>
        <td>RF</td>
        <td>RADIO Act</td>
        <td>GPIO_2</td>
    </tr>
    <tr>
        <td>DS4</td>
        <td>WAN</td>
        <td>Link/Act</td>
        <td>NA</td>
    </tr>
    <tr>
        <td>DS14</td>
        <td>LAN1</td>
        <td>Link/Act</td>
        <td>NA</td>
    </tr>
    <tr>
        <td>DS12</td>
        <td>LAN2</td>
        <td>Link/Act</td>
        <td>NA</td>
    </tr>
    <tr>
        <td>DS13</td>
        <td>LAN3</td>
        <td>Link/Act</td>
        <td>NA</td>
    </tr>
    </table>

#### Additional hardware informations
- I have two wireless cards TP-Link TL-WN360G. One is used as client to connect to my WISP, the other
  is used as AP for my home network.
- I have a 8GB USB flash drive connected to the USB port and I have configured extroot (rootfs on external storage),
  so the entire system is booted from this device. The entire configuration is done in `/etc/config/fstab`, so if
  you don't want this, change the mount target from `/` to `/mnt` (or something else). Also if you use the Backfire
  release or versions of Trunk older than `r26109`, mounting the external storage as `/` is not possible.
