# Kernel .config file for fuzzing with Syzkaller

Linux .config files to start fuzzing with Syzkaller.

## Why this?
Basically I'm lazy and don't wanna edit .config files evey time by hand. 
Storing stuff on GitHub makes easy to find them when you need.

## How to use?

Clone the repository:

```
git clone https://github.com/diaul/syzkaller
```

Move inside the directory: 

```
cd syzkaller
```

Copy the files inside the following path:

```
cp syzkaller_base.config $KERNEL_SRC/kernel/config/
cp syzkaller_enhance.config $KERNEL_SRC/kernel/config/
```

Where $KERNEL_SRC is the extracted source of the kernel you want to test.

Move to the Kernel source directory:

```
cd $KERNEL_SRC
```

Configure the Kernel: 

```
make defconfig 
make kvm_guest.config

make syzkaller_base.config 
```

or:

```
make syzkaller_enhance.config
```

based on your needs

Build the kernel:

```
make -j`nproc`
```

## References

The original source comes from official Syzkaller documentation:

* https://github.com/google/syzkaller/blob/master/docs/linux/setup_ubuntu-host_qemu-vm_x86-64-kernel.md
* https://github.com/google/syzkaller/blob/master/docs/linux/kernel_configs.md
 
## Notes 

There are further examples of syz-kconf automatic generated .config files in this folder: 

* https://github.com/google/syzkaller/tree/master/dashboard/config/linux

Should give a loot at it ...
