# Nokia_G-1425-MA

I have a Nokia G-1425-MA from a NEPALESE ISP. The router is fully locked when it was inservice.

Opening the Back of the router , There is a serial Port to connect to. After connecting to the router The following is the bootlog

refer to bootlog here

#  GE Rext AnaCal Done! (4)(0x1c)
#  Press enter in 3 secs to enter boot command mode.

pressing any buttons

it prompts for username and password

> Username : telecomadmin
> Password : nE7jA%5m


here we can press ? to get help




most things here aren't very useful but ritool 

# ritool dump

> ?                                   Print out help messages.
> help                                Print out help messages.
> reset                               reset.
> ritool                              ritool.
> flashbin                            flashbin.
> go                                  Booting the linux kernel.
> decomp                              Decompress kernel image to ram.
> memrl <addr>                        Read a word from addr.
> memwl <addr> <value>                Write a word to addr.
> dump <addr> <len>                   Dump memory content.
> jump <addr>                         Jump to addr.
> flash <dst> <src> <len> <oob>       Write to flash from src to dst(oob: write nand oob if 1).
> nander <dst> <len> <oob>            Erase flash from dst(oob: force erase oob if 1).
> imginfo                             Show images info.
> spinand_rwtest                      Flash Test
> bdstore <flash dst> <bin src>       Do backdoor config store
> bdshow                              Show backdoor config
> bdswitch[1|0]                       Enable or disable backdoor function
> ddrcalswitch[1|0]                   Enable or disable ddr calibration funciton
> drambistswitch[0|1|2]               disable or enable, and quick or normal test
> xmdm <addr> <len>                   Xmodem receive to addr.
> miir <phyaddr> <reg>                Read ethernet phy reg.
> miiw <phyaddr> <reg> <value>        Write ethernet phy reg.
> cpufreq <freq num> / <m> <n>        Set CPU Freq <156~450>(freq has to be multiple of 6)
> ipaddr <ip addr>                    Change modem's IP.
> httpd                               Start Web Server


