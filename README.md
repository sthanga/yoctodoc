# Yoctodoc
yocto-study-doc-remember 
web link for refer the md document format to create the doc with different fonts and colour/ paragraph [md doc formats](https://www.inflectra.com/Support/KnowledgeBase/KB725.aspx).
Refer [markdown systax](https://www.markdownguide.org/basic-syntax).
<br>
**Latest kernel source file in bootlin see** [Kernel link](https://elixir.bootlin.com/linux/v6.6.1/A/ident/ioctl)
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

**<p> root file system structure which is contains below folders </p>**

* bin  -> system runable binary file?    

* boot -> /boot-directory contains boot configuration for system boot process

* dev  -> device file and memory file 

* etc  -> systemd and service files

* home -> workspace for user  

* lib  -> shared libraries, application includes are present here.

* media->  

* mnt  -> ssd / memeory mount 

* proc -> system debug and system kernel information

* root -> user root

* run  ->important things to run at boot like wifi, bluetooth, initramfs, alsa,   

* sbin ->important things to run at binary   

* srv  -> common directory to use(we can put anything to fetch for appln)

* sys  -> interface for debugging and adding at kernel    

* tmp  -> to be studied

* usr  -> all added binaries, system binaries will present    

* var  -> variable files that files will change frequently, system writting data will happen here.

* symlink -> ref new generate file i.e point to new updates file(image file to link current updated file)

# Bitbake related Commands :
In Yocto, `bitbake` is the primary tool for building packages and images. Here’s a list of commonly used `bitbake` commands:

### 1. **Build Commands**
- **Build an image**:
  ```bash
  bitbake <image-name>
  ```
  Example: Build a core image:
  ```bash
  bitbake core-image-minimal
  ```

- **Build a specific recipe/package**:
  ```bash
  bitbake <recipe-name>
  ```
  Example: Build a specific package:
  ```bash
  bitbake busybox
  ```

### 2. **Cleaning and Rebuilding**
- **Clean all files for a recipe/package**:
  ```bash
  bitbake -c clean <recipe-name>
  ```
  Example: Clean all files for `busybox`:
  ```bash
  bitbake -c clean busybox
  ```

- **Clean all and then build**:
  ```bash
  bitbake -c cleansstate <recipe-name>
  ```
  This will clean both the work directory and the shared state (sstate) cache.

- **Rebuild a package after cleaning**:
  ```bash
  bitbake -c cleanall <recipe-name>
  bitbake <recipe-name>
  ```

- **Recompile a recipe**:
  ```bash
  bitbake -f -c compile <recipe-name>
  ```

### 3. **Task Management**
- **Execute a specific task**:
  ```bash
  bitbake -c <task-name> <recipe-name>
  ```
  Example: Compile a recipe:
  ```bash
  bitbake -c compile busybox
  ```

  Common tasks:
  - `fetch`: Downloads the source files for the recipe.
  - `configure`: Configures the source for building.
  - `compile`: Compiles the source code.
  - `install`: Installs compiled code to a staging area.
  - `package`: Packages the software.
  - `populate_sysroot`: Installs files into the sysroot.
  - `do_rootfs`: Creates the root filesystem for an image.

### 4. **Information Commands**
- **Show dependencies of a recipe**:
  ```bash
  bitbake -g <recipe-name>
  ```
  This will generate two files, `pn-buildlist` and `task-depends.dot`, which show task dependencies.

- **Show available tasks for a recipe**:
  ```bash
  bitbake -c listtasks <recipe-name>
  ```
  Example:
  ```bash
  bitbake -c listtasks busybox
  ```

- **Show recipe variables**:
  ```bash
  bitbake -e <recipe-name>
  ```
  This command shows all variables and their values for the specified recipe.

- **Show summary of build environment**:
  ```bash
  bitbake -s
  ```

### 5. **Image Management**
- **Rebuild the image without rebuilding all dependencies**:
  ```bash
  bitbake <image-name> -c rootfs
  ```

- **Rebuild the image and package everything**:
  ```bash
  bitbake <image-name> -c populate_sdk
  ```

- **Create an SDK for the image**:
  ```bash
  bitbake <image-name> -c populate_sdk
  ```

### 6. **Bitbake Options**
- **Dry run**: See what tasks would be executed without running them.
  ```bash
  bitbake -n <recipe-name>
  ```

- **Run in debug mode**: Output more detailed information.
  ```bash
  bitbake -v <recipe-name>
  ```

- **Print all debug output**:
  ```bash
  bitbake -D <recipe-name>
  ```

- **Stop at the first error**:
  ```bash
  bitbake -k <recipe-name>
  ```

### 7. **Working with Layers**
- **Check available layers**:
  ```bash
  bitbake-layers show-layers
  ```

- **Show available recipes**:
  ```bash
  bitbake-layers show-recipes
  ```

- **Show the version of a specific recipe**:
  ```bash
  bitbake-layers show-recipes <recipe-name>
  ```

- **Add a layer**:
  ```bash
  bitbake-layers add-layer <layer-path>
  ```

- **Remove a layer**:
  ```bash
  bitbake-layers remove-layer <layer-name>
  ```

These commands will help you build, clean, and manage your Yocto project using Bitbake. Let me know if you need further details on any specific command or process!

- **Image Size/Binary size**:
  ```bash
  wc -c <Binary Name>
  Ex :
  wc -c ipmitool
  3014528 ipmitool
```
It looks like you're listing the available BitBake-related commands on your system. BitBake is a task execution engine typically used by the Yocto Project to build packages, images, or SDKs for embedded Linux systems.

Here's a brief explanation of the listed commands:

### Primary Commands:
1. **bitbake**:  
   The main BitBake command. It executes tasks to build recipes. You specify the target (usually a recipe or image) to build:
   ```bash
   bitbake <target>
   ```
   Example:
   ```bash
   bitbake core-image-minimal
   ```

### Utility Commands:
2. **bitbake-diffsigs**:  
   Compares the task signature (checksum) differences between two builds. This is helpful when debugging why certain tasks are being re-executed:
   ```bash
   bitbake-diffsigs <sig1> <sig2>
   ```

3. **bitbake-dumpsig**:  
   Dumps the content of a BitBake task signature file to understand what affects a task’s execution:
   ```bash
   bitbake-dumpsig <sigfile>
   ```

4. **bitbake-getvar**:  
   Retrieves the value of a variable in a BitBake environment. You can check variable values for recipes, e.g.:
   ```bash
   bitbake-getvar <recipe> <variable>
   ```

5. **bitbake-hashclient**:  
   Used to query or interact with the BitBake hash server that tracks task signatures.

6. **bitbake-hashserv**:  
   Manages the task hash server for improving task execution efficiency across builds.

7. **bitbake-layers**:  
   Helps manage and inspect BitBake layers. You can check for missing or conflicting layers, or visualize dependencies:
   ```bash
   bitbake-layers show-layers
   ```

8. **bitbake-prserv**:  
   Stands for "Priority Server". It's used to manage recipe PR (package release) numbers across different build environments to avoid manual management.

9. **bitbake-selftest**:  
   Runs the BitBake self-tests to check the integrity of the BitBake environment and functionality:
   ```bash
   bitbake-selftest
   ```

10. **bitbake-server**:  
    The background server process that handles BitBake tasks. Typically started by BitBake itself and is not invoked manually.

11. **bitbake-worker**:  
    Used internally by the BitBake server to execute tasks in parallel.

### Toaster-related Commands:
12. **toaster**:  
    A web interface for BitBake and Yocto, allowing you to manage builds, layers, and recipes through a browser.

13. **toaster-eventreplay**:  
    Replays Toaster events for debugging and viewing how BitBake tasks were processed.

### Git-related Command:
14. **git-make-shallow**:  
    A utility for creating shallow Git clones. This can be helpful when fetching repositories for building recipes in Yocto, reducing download size by limiting the history fetched.

---

If you're setting up or troubleshooting BitBake, feel free to ask specific questions related to any command or process.
