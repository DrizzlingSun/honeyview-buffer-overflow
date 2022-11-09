# honeyview buffer overflow
## Overview
- Manufacturer's website information： https://www.bandisoft.com/ 

- Firmware download address：https://cn.bandisoft.com/honeyview/dl.php?web

## Affected version
- Honeyview ver<=5.50

- Honeyview-portable ver<=5.50

## Vulnerability details
![image](https://user-images.githubusercontent.com/65169560/200780665-a956fceb-3154-4dda-9659-06968ad5956e.png)

after reading POC file

![image](https://user-images.githubusercontent.com/65169560/200780769-9322349d-e1e0-4282-9238-55a6664a26c9.png)

![image](https://user-images.githubusercontent.com/65169560/200780852-b2d0205c-6154-4967-81cd-e27b4d3abc5c.png)

![image](https://user-images.githubusercontent.com/65169560/200781962-f9305f55-15d1-476f-8a43-86cb3676cbc2.png)

Honeyview can directly view images in the compressed package such as Zip, etc.but when a malformed zip file is read into the software with an incorrect filename extension (such as bmp, jpg, etc.), it will cause crash. The reason for the crash is that after reading the file, the rax at this time will be set to 0, and when the function wants to verify the address [rax], it will crash because the address is illegal, and the offset of the specific location is 001f1b73.

## Recurring vulnerabilities and POC
to exploit vulnerability, some one must open a crafted zip file that filename extension is modified as bmp、jpg. So just read the POC with Honeyview, than it will crash.
![image](https://user-images.githubusercontent.com/65169560/200785275-1baf0a76-451c-40a3-a90d-bb02b59610eb.png)

POC attack effect

Finally, you can write exp, which can achieve a very stable effect of obtaining the root shell.

## Author
Drizzling_Sun @KRlab
