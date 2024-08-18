# Yoctodoc
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

3. menuconfig for uboot driver selection
     + **"bitbake -c menuconfig u-boot"**
     + **"bitbake -c menuconfig u-boot-aspeed-sdk"**
![image](https://github.com/user-attachments/assets/a81151ca-4706-499f-a9d8-d40567e63ad0)

4. To remove the images in the build o/p's :
     + **"bitbake -c cleansstate obmc-phosphor-image"**
5. To clean the packages:
        + **"bitbake -c cleanall ipmitool /or packagename "**
     note: can do sigle commands as
   + __bitbake -c cleansstate obmc-phosphor-image && bitbake obmc-phosphor-image__
6. Go to source file in the build system
      + **bitbake -c devshell virtual/kernel** or use **bitbake -c devshell packagename**
7. if do one package to compile
       + **bitbake virtual/kernel**  or 
       + **bitbake ipmitool**
       + **bitbake i2capplication**
   it will compile that respective package only.
8. create the package into workspace
   + to bring into  workspace - **devtool modify ipmitool /or packagename**
   + to reset from the workspace - **devtool reset ipmitool /or packagename**
9. dump command to view 
    * __fdtdump__  i.e file of dtb
    * __objdump__  i.e file of object
    * __*tcpdump*__  i.e  file of tcp
    * __hexdump__  i.e file of hex
10. to crate a meta-layer in the root folder 
     **bitbake-layers create-layer ../../meta-custom** 
11. to add meta-layer into conf/bblayers.conf
    + **bitbake-layers add-layer ../../meta-custom**
12. to show the adder layers / cross check that to added layers in the layers
     + **bitbake-layers show-layers**
     + **bitbake-layers  then below listed commands to be take** <br>
        __*(choose from 'layerindex-fetch', 'layerindex-show-depends', 'add-layer', 'remove-layer', 'flatten', 'show-layers', 'show-overlayed', 'show-recipes', 'show-appends', 'show-cross-depends', 'save-build-conf', 'create-layer', 'create-layers-setup')*__
13. #### scp command
    + **scp ./filename  root@192.168.1.50:/usr/bin** <br>
     it is pasting the binary/ files into that location if one to another system/os
14. #### ssh command <br>
     if the system/ laptop is connection same network point .i.e lan /wifi.
      then the device can connect through below command <br>
    + **ssh root@192.168.1.20**
# Rofs @ linux - yocto
