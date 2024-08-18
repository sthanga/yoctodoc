# yoctodoc
yocto-study-doc-remember 
web link for refer the md document format to create the doc with different fonts and colour/ paragraph [md doc formats](https://www.inflectra.com/Support/KnowledgeBase/KB725.aspx).
Refer [marddown systax](https://www.markdownguide.org/basic-syntax).
## yocto Learned commands.
1. for openbmc build commands;
     **"bitbake obmc-phosphor-image"**
   it will build and create the image files respect openbmc machine selection in the /conf/local.conf.
2. menuconfig file commands for kernel driver selection
     __"bitbake -c menuconfig virtual/kernel"__
                 or  
    **"bitbake -c menuconfig linux-aspeed"**
