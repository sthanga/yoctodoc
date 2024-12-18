# Linux Kernel learnings *****
### Linux 1969
``` sh
Directories in the Root of the Kernel Source Tree
Directory            Description
arch                 Architecture-specific source
block                Block I/O layer
crypto               Crypto API
Documentation        Kernel source documentation
drivers              Device drivers
firmware             Device firmware needed to use certain drivers
fs                   The VFS and the individual filesystems
include              Kernel headers
init                 Kernel boot and initialization
ipc                  Interprocess communication code
kernel               Core subsystems, such as the scheduler
lib                  Helper routines
mm                   Memory management subsystem and the VM
net                  Networking subsystem
samples              Sample, demonstrative code
scripts              Scripts used to build the kernel
security             Linux Security Module
sound                Sound subsystem
usr                  Early user-space code (called initramfs)
tools                Tools helpful for developing Linux
virt                 Virtualization infrastructure
```

### linux familier commands
```bash
# for i2c bus channel and devices
cd /sys/bus/i2c/devices/i2c-x/

# To initate a new device on the i2c channel
echo drivername 0x20 > /sys/bus/i2c/devices/i2c-x/new_device
```
``` bash
# Kernel driver details.
cat /proc/sys/kernel/printk       #Ensure the printk enabled or not
echo 8 > /proc/sys/kernel/printk  #Ensure the printk enabled or not
rmmod ipmi_ipmb                   # remove the ipmi_ipmb driver module
depmod -a                  #to remove the all dependency of modprobe module
lsmod           
ls -l /dev/ipmi0           #list the device file
dmesg | tail -n 50         # check the kernel last 50 messages

ls /lib/modules/5.15.71+g95448dd0dc9b/kernel/drivers/char/ipmi/    # list module to be installed
modprobe ipmi_si type=i2c addrs=0x15
insmod ipmi_si        # module name 
/lib/modules/$(uname -r)/modules.dep
# example below
kernel/drivers/char/ipmi/ipmi_msghandler.ko:
kernel/drivers/char/ipmi/ipmi_devintf.ko: kernel/drivers/char/ipmi/ipmi_msghandler.ko
kernel/drivers/char/ipmi/ipmi_si.ko: kernel/drivers/char/ipmi/ipmi_msghandler.ko
kernel/drivers/char/ipmi/ipmi_ssif.ko: kernel/drivers/char/ipmi/ipmi_msghandler.ko
kernel/drivers/mtd/tests/mtd_speedtest.ko:
kernel/drivers/mtd/tests/mtd_stresstest.ko:

# below's are device reupdate
udevadm trigger --subsystem-match=ipmi
udevadm control --reload
udevadm trigger
udevadm
udevadm trigger

dmesg | tail -n 50
modprobe ipmi_si type=i2c addrs=0x15

zcat  /prog/config.az  | grep IPMI    # to check the driver module addition status 
cat /proc/devices | grep ipmidev      # to check major number of the ipmidev module
   
mknod /dev/ipmi0 c 243 0             # manually add the device module         
chmod 600 /dev/ipmi0                 # give the permission, 777, 644, 666 600 etc,

```
``` bash
# dtb file to dts file convertion and update

ensure :  install device-tree-compiler

dtc -I dtb -O dts -o output.dts input.dtb

Explanation:

-I dtb: Specifies the input format (DTB in this case).
-O dts: Specifies the output format (DTS).
-o output.dts: Specifies the name of the output DTS file.
input.dtb: Specifies the input DTB file you want to convert.

```
