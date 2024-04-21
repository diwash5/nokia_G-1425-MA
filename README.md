# Nokia G-1425-MA

I have a Nokia G-1425-MA from a NEPALESE ISP. The router is fully locked when it was inservice.

Opening the Back of the router , There is a serial Port to connect to. After connecting to the router The following is the bootlog

refer to bootlog here

  GE Rext AnaCal Done! (4)(0x1c)
  Press enter in 3 secs to enter boot command mode.
  
pressing any buttons.it prompts for username and password

```
 Username : telecomadmin
 Password : nE7jA%5m
```

here we can press ? to get help


```

?                                   Print out help messages.
help                                Print out help messages.
reset                               reset.
ritool                              ritool.
flashbin                            flashbin.
go                                  Booting the linux kernel.
decomp                              Decompress kernel image to ram.
memrl <addr>                        Read a word from addr.
memwl <addr> <value>                Write a word to addr.
dump <addr> <len>                   Dump memory content.
jump <addr>                         Jump to addr.
flash <dst> <src> <len> <oob>       Write to flash from src to dst(oob: write nand oob if 1).
nander <dst> <len> <oob>            Erase flash from dst(oob: force erase oob if 1).
imginfo                             Show images info.
spinand_rwtest                      Flash Test
bdstore <flash dst> <bin src>       Do backdoor config store
bdshow                              Show backdoor config
bdswitch[1|0]                       Enable or disable backdoor function
ddrcalswitch[1|0]                   Enable or disable ddr calibration funciton
drambistswitch[0|1|2]               disable or enable, and quick or normal test
xmdm <addr> <len>                   Xmodem receive to addr.
miir <phyaddr> <reg>                Read ethernet phy reg.
miiw <phyaddr> <reg> <value>        Write ethernet phy reg.
cpufreq <freq num> / <m> <n>        Set CPU Freq <156~450>(freq has to be multiple of 6)
ipaddr <ip addr>                    Change modem's IP.
httpd                               Start Web Server

```
most things here aren't very useful but ritool 

# ritool dump
```
Format:00
MfrID:NBEL
Factorycode:02
HardwareVersion:3FE49170AAAA
ICS:01
YPSerialNum:    NBELEB20CA88
CleiCode:0000000000
Mnemonic:G-1425-MA
ProgDate:052016
MACAddress:d4:4f:67:4c:94:3c
DeviceIDPref:3030
SWImage:3030
OnuMode:0003
Mnemonic2:A
Password:30303030303030303030
G984Serial:eb20ca88
HWConfiguration:3030303030303030
PartNumber:3FE49170AAAA
Spare4:303030303030303030303030
Checksum:e1e3
InserviceReg:3030
UserName:            user
UserPassword:00000000
MgntUserName:0000000000000000
MgntUserPassword:00000000
SSID-1Name:             dws
SSID-1Password:00000000
SSID-2Name:0000000000000000
SSID-2Password:00000000
OperatorID:RILT
SLID:30303030303030303030303030303030
CountryID:00
Spare5:303030303030
Checksum1:18e8
Spare6:3030
RollbackFlag:3030
SSN:            M162135ALU00055108
DeviceIDFormat:00
BoardID:             G1425MA
```

The above is actually my now current config cause i already lost the original . Some are Borrowed and Some were found in logs after.
if the BoardID is wrong , the router Wont bootup . there are some options we may look after.
I've tried 
