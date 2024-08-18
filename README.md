# yoctodoc
yocto-study-doc-remember 
web link for refer the md document format to create the doc with different fonts and colour/ paragraph [md doc formats](https://www.inflectra.com/Support/KnowledgeBase/KB725.aspx).
Refer [marddown systax](https://www.markdownguide.org/basic-syntax).
## yocto Learned commands.
1. for openbmc build commands;
     **"bitbake obmc-phosphor-image"**
   it will build and create the image files respect openbmc machine selection in the /conf/local.conf.
2. menuconfig file commands for kernel driver selection
    + __"bitbake -c menuconfig virtual/kernel"__
                 or 
   + **"bitbake -c menuconfig linux-aspeed"**
   
   ![image](https://github.com/user-attachments/assets/2846c607-4c61-4ef8-8bb9-821fd3960e55)

4. menuconfig for uboot driver selection
     + **"bitbake -c menuconfig virtual/kernel"**
![image](https://github.com/user-attachments/assets/a81151ca-4706-499f-a9d8-d40567e63ad0)

5. To remove the images in the build o/p's :
     + **"bitbake -c cleansstate obmc-phosphor-image"**
6. To clean the packages:
        + **"bitbake -c cleanall ipmitool /or packagename "**
     note: can do sigle commands as
   + __bitbake -c cleansstate obmc-phosphor-image && bitbake obmc-phosphor-image__
7. Go to source file in the build system
      + **bitbake -c devshell virtual/kernel** or use **bitbake -c devshell packagename**
8. if do one package to compile
       + **bitbake virtual/kernel**  or 
       + **bitbake ipmitool**
       + **bitbake i2capplication**
   it will compile that respective package only.
9. create the package into workspace
10.    
