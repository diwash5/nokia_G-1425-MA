# Nokia G-1425-MA

I have a Nokia G-1425-MA from a NEPALESE ISP. The router is fully locked when it was inservice.

Opening the Back of the router , There is a serial Port to connect to. After connecting to the router The following is the bootlog
The baudrate is 115200

refer to bootlog here
```
  GE Rext AnaCal Done! (4)(0x1c)
  Press enter in 3 secs to enter boot command mode.
```
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
we can dump by ```ritool dump```

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
OperatorID is responsible for Changing configs . I've found that ```RILT``` will Turn on the WEB as well as will be on English. We can also choose ```CMCC``` which is in Chinese .

we can set it by
```ritool set OperatorID RILT```


It is best to keep a backup of this dump.
 
 ```go```to Continue the boot process

Now the web is active . if it isn't you may need to restart a few times or even reset by using command ```reset```

## Shell Authentication
If the Web is not Active We can get inside from shell to get access to the router
After pressing ```go```or just router to boot . After 5-7 minutes We get access to ABS User CLI which is pretty bad 
```
  enable    Turn on privileged mode command
  help      Description of the interactive help system
  hw_nat    platform special network commands,eg. hg_nat -g
  ifconfig  ifconfig is used to configure, or view the configuration of, a network interface.
  ip        show / manipulate routing, devices, policy routing and tunnels
  list      Print command list
  nslookup  The nslookup command is used to query Internet name servers interactively for information
  ping      Send echo messages
  ps        Scan a host, print all open ports
  route     show / manipulate the IP routing table
  show      system display
  top       Provide a view of process activity in real time
```


use ```enable``` now ```help```


```
  configure  Configuration from vty interface
  disable    Turn off privileged mode command
  exit       Exit current mode and down to previous mode
  help       Description of the interactive help system
  list       Print command list
  reboot     Reboot system.
  shell      start shell, need to input the user and password
  show       Show information from vty interface
  terminal   Set terminal line parameters
```

use the command ```shell```which prompts for password . Put in
```LA(ImvZx%8```

 viola , you're already on shell . We will talk about changing configs later on.
## WEB AUTHENTICATION

It should be at 192.168.1.1 when in RILT and 192.168.254.254 in other operatorID

```
Username : classicadmin
Password : Cr3d3nti@lofNok!aONT0061_P@SSW)RD
```
The username and password for Non-Classictech routers seems to be

```
Username : CMCCAdmin
Password : aDm8H%MdA
```

there is user level username and password but is very limited .
```
username : admin
password : admin
```

## Telnet

login as classicadmin then visit the site ```<yourrouterip>/system.cgi?telnet``` and toggle the switch
Telnet will be available at port ```2333```

Logging into telnet . 
```
Username : user
Password : 00000000
```

## Getting the Config


form telnet you can just ```cfgcli dump ```

whereas from web you can go to ```<yourrouterip>/dumpdatamodel.cgi```


### Restoring the Config

I dont have a Way to restore the config file but you can use the shell to change expects of it . you'll need to factory reset each time to apply them though
To get

``` 
cfgcli -g InternetGatewayDevice.DeviceInfo.X_CT-COM_ServiceManage.SSHEnable
```

To set
```
cfgcli -s InternetGatewayDevice.DeviceInfo.X_CT-COM_ServiceManage.SSHEnable True
```



