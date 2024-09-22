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
  ```link
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


## **GDB (GNU Debugger) server and client configuration** involves setting up a remote debugging session where the target system (e.g., an embedded system) runs the GDB server, and the development system (your local machine) runs the GDB client to control the debugging process.

Here’s a step-by-step guide on how to configure GDB server and client:

### **Step 1: Set up GDB on the Target (Server)**
The **GDB server** runs on the target system, which can be a remote machine or an embedded device.

1. **Install GDB Server**:
   On the target machine, you need `gdbserver`. If it is not installed, you can install it using a package manager:
   
   - **For Debian/Ubuntu**:
     ```bash
     sudo apt-get install gdbserver
     ```
   
   - **For Red Hat/CentOS**:
     ```bash
     sudo yum install gdb-gdbserver
     ```

2. **Run the GDB Server**:
   Start `gdbserver` on the target machine with the following command:
   
   ```bash
   gdbserver :<port> <program> [program-args]
   ```
   - `<port>`: The port number on which `gdbserver` will listen (e.g., 1234).
   - `<program>`: The program you want to debug.
   - `[program-args]`: (Optional) Arguments for the program being debugged.

   Example:
   ```bash
   gdbserver :1234 ./my_program arg1 arg2
   ```

   Alternatively, if you want to attach `gdbserver` to an already running process, use:
   ```bash
   gdbserver :1234 --attach <pid>
   ```

### **Step 2: Set up GDB on the Host (Client)**
The **GDB client** runs on your development machine and connects to the `gdbserver` on the target system.

1. **Install GDB**:
   On your host machine, install `gdb` if it's not already installed.
   
   - **For Debian/Ubuntu**:
     ```bash
     sudo apt-get install gdb
     ```
   
   - **For Red Hat/CentOS**:
     ```bash
     sudo yum install gdb
     ```

2. **Start GDB and Connect to the Server**:
   Start GDB on the host machine and specify the program binary (the one on the host):
   
   ```bash
   gdb ./my_program
   ```

   Once inside GDB, connect to the remote target via `gdbserver`:
   
   ```bash
   (gdb) target remote <target-ip>:<port>
   ```
   - `<target-ip>`: The IP address of the target machine.
   - `<port>`: The port number that `gdbserver` is listening on (e.g., 1234).

   Example:
   ```bash
   (gdb) target remote 192.168.1.100:1234
   ```

3. **Load the Symbols** (Optional):
   If you have compiled the program with debugging symbols (using the `-g` flag), you may want to load these symbols:
   
   ```bash
   (gdb) symbol-file /path/to/executable
   ```

### **Step 3: Debugging the Program**
Once connected, you can use GDB's standard debugging commands:
- `b <function>`: Set a breakpoint.
- `c`: Continue execution.
- `n`: Step over a function.
- `s`: Step into a function.
- `bt`: Backtrace (see the call stack).
- `p <variable>`: Print the value of a variable.

### **Example: Full Process**
1. **On Target (Server)**:
   ```bash
   gdbserver :1234 ./my_program
   ```

2. **On Host (Client)**:
   ```bash
   gdb ./my_program
   (gdb) target remote 192.168.1.100:1234
   (gdb) b main
   (gdb) c
   ```

### **Step 4: Exit and Disconnect**
To disconnect from the GDB server:
- Simply type `q` or `quit` in the GDB client.

The GDB server will automatically stop once the client disconnects or the program terminates.

### **Additional Options**
- **Debugging with `gdb-multiarch`**:
  If you're debugging an embedded system with a different architecture, you might need to use `gdb-multiarch` on the host to handle cross-architecture debugging.
  
  Example for ARM:
  ```bash
  sudo apt-get install gdb-multiarch
  gdb-multiarch ./my_program
  ```

### **Debugging a Kernel (Optional)**:
If you are debugging a kernel, you need to use `kgdb` on the target and follow a similar process, but the configuration is more involved, often requiring kernel patches and boot parameters.

---

By following these steps, you can set up remote debugging using GDB on both client and server, allowing you to inspect and control the execution of programs on remote systems.

### **Weblink(debug)**:
```bash
.[web details link](https://sergioprado.blog/debugging-the-linux-kernel-with-gdb/)
.[youtube link ](https://www.youtube.com/watch?v=C55_fbAb_24)
```

# Ctags
***If you're currently in `sudo su` or a root shell and want to return to a normal user session, you can exit the root shell by using the following command***
`ctags` is a tool used to generate an index (or tag) file of various source code elements, such as function definitions, variable names, class definitions, etc., from source files. This tag file can then be used by text editors and IDEs to quickly navigate through the codebase.

### Installing `ctags`

If you don't have `ctags` installed on your system, you can install it using:

- **Ubuntu/Debian**:
  ```bash
  sudo apt install exuberant-ctags
  ```

### Using `ctags`

To add `ctags` to your project, follow these steps:

1. **Generate Tags File**:
   Navigate to the root of your source code directory and run:
   ```bash
   ctags -R .
   ```
   This command generates a `tags` file by recursively scanning the current directory (`.`) for all source code files.

2. **Use in Editors**:
   - **Vim**: With `ctags`, you can use commands like `:tag <function_name>` to jump to the definition of a function or variable. You can use `Ctrl-]` to jump to the tag under the cursor.
   - **Emacs**: Use `M-.` to jump to a definition.
   - **Other Editors**: Many IDEs and text editors (like Sublime Text or VSCode with plugins) can utilize `ctags` for code navigation.

### Example:
Let’s say you have a simple project structure like:

```
project/
├── main.c
└── helper.c
```

You can run:
```bash
cd project
ctags -R .
```

This will create a `tags` file in the `project/` directory, and you'll be able to use navigation features in your text editor to jump to definitions in `main.c`, `helper.c`, etc.

### Customizing `ctags`

You can customize `ctags` with various options:

- **Include certain file types**:
  ```bash
  ctags -R --languages=C,C++ .
  ```

- **Excluding certain directories**:
  ```bash
  ctags -R --exclude=.git --exclude=build .
  ```

- **Generate tags for specific files**:
  ```bash
  ctags file1.c file2.c
  ```

Once set up, `ctags` makes it much easier to navigate large codebases by jumping to definitions or references within the code.



