# MacBook PRO 13 (mid-2012) EFI BIOS Password Reset

This tutorial can be applied to also other Apple products. Just follow the steps below.

## Tools used

1) Multi-Functional Programmer, RT809F
2) Hot-air gun
3) Soldering station
4) Hex Editor, HxD
5) [UEFITool](https://www.alisaler.com/category/softwares/uefi-tools/)

### Look for EEPROM

Fist of all you need to find EEPROM somewhere on the main board. In my case MacBook PRO 13 (mid-2012) EEPROM is located next to the fan on the edge of the main board. Marking on the IC is 25R064A. According to RT809F multi-functional programmer this is N25Q064AX3E@S08N memory chip from Numonyx. 

![28R064A](https://forum.cxem.net/uploads/monthly_2016_12/macmini.thumb.jpg.34c6cf8ff01d56a1a830dfead6247261.jpg?raw=true)

![EEPROM location](https://www.allservice.ro/forum/images/A1278-2012.jpg?raw=true)

I tried to use cips but it didn't work out for me. So the only way was to remove EEPROM from the main board and put it into a multi-functional programmer and read it's content. That worked well.

Open bin file in HxD hex editor. In the opened file look for $SVS characters. In my case $SVS starts at address: 0x00692050. Next question was how much data I should delete. I couldn't find any trustable source on the internet as each example was done on different MacBooks. I tried my luck and deleted all data up to the place where a lot of FF appiers.

Uploaded bin file back to EEPROM and soldered back. Started the MacBook and lucky me, my password was gone.

## References

- [EEPROM Location on different MacBooks](https://www.allservice.ro/forum/viewtopic.php?t=2724)
- [Video](https://www.youtube.com/watch?v=oI3V5KKKmCI)
- [Reflashing EFI ROM](https://gist.github.com/willzhang05/e5b5563cdc65514dfb7ca131e03ca4b2)