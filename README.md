# how to upgrade and recovery router image using tftp server
## HOW TO DOWNLOAD IMAGE FROM SERVER TO ROUTER ON PACKET TRACER.

## Verify Network Connectivity
Ensure that the router can reach the TFTP server. You can test this by using the ping command from the router.
R1#PING 10.10.10.10

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.10, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/1 ms

## Check Available Space on Router
Before downloading, ensure that there is enough space in the router’s flash memory to store the image. Using the command dir.
R1#dir flash:
Directory of flash0:/

    3  -rw-    33591768          <no date>  c2900-universalk9-mz.SPA.151-4.M4.bin
    4  -rw-         696          <no date>  demo
    2  -rw-       28282          <no date>  sigdef-category.xml
    1  -rw-      227537          <no date>  sigdef-default.xml

255744000 bytes total (221895717 bytes free)
R1#
## Check the image from router to use as a backup
### Use the command show flash
R1#show flash

System flash directory:
File  Length   Name/status
  3   33591768 c2900-universalk9-mz.SPA.151-4.M4.bin
  4   696      demo
  2   28282    sigdef-category.xml
  1   227537   sigdef-default.xml
[33848283 bytes used, 221895717 available, 255744000 total]
249856K bytes of processor board System flash (Read/Write

## Copy the flash to the TFTP server using the following command:
R1#copy flash: TFTP: 
Source filename []? c2900-universalk9-mz.SPA.151-4.M4.bin
Address or name of remote host []? 10.10.10.10
Destination filename [c2900-universalk9-mz.SPA.151-4.M4.bin]? 

Writing c2900-universalk9-mz.SPA.151-4.M4.bin...!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
[OK - 33591768 bytes]

33591768 bytes copied in 0.674 secs (5232933 bytes/sec)





##Next, go to the TFTP server and verify if the image has been successfully copied.
 
![image](https://github.com/user-attachments/assets/33082437-c196-4519-b3bc-82a12b46c144)

##The router's backup image is now stored on the TFTP server.


###Now, we need to delete the iOS image from the router. After that, we'll download the iOS image from the TFTP server to restore the backup.

###Use the following command to delete the iOS image from the router:


R1#delete c2900-universalk9-mz.SPA.151-4.M4.bin
Delete filename [c2900-universalk9-mz.SPA.151-4.M4.bin]?
Delete flash:/c2900-universalk9-mz.SPA.151-4.M4.bin? [confirm]

##Now the router is without IOS image and it is on Romon  status.

 
##Since your router is now in Romon mode and doesn't have an iOS image, you'll need to load a new iOS image from a TFTP server. Here’s a step-by-step guide on how to proceed:

##1. Verify Network Connectivity in Romon Mode:
Before you can transfer the iOS image, ensure that the router can communicate with the TFTP server. First, set the router's IP configuration:

##Set the router's IP address:

![image](https://github.com/user-attachments/assets/64fc568e-cfba-4864-98fc-c5ca59c26bf5)




 
##Once the image has been downloaded successfully, instruct the router to boot from the new iOS image.

rommon> boot flash: c2900-universalk9-mz.SPA.151-4.M4.bin
##Then use command show version to the image you downloaded.
![image](https://github.com/user-attachments/assets/f568008a-7081-4522-9008-f0f86252bede)

 
##Or show flash and see the image .

 ![image](https://github.com/user-attachments/assets/d23ed051-e9fa-48c5-906f-8b929f5f6f48)










