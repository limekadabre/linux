CMPE283 – VIRTUALIZATION TECHNOLOGIES
ASSIGNMENT – 1 : DISCOVERING VMX FEATURES

HOST OS : Windows
RAM : 8 GB
Processor : Intel core i5

* Install VMware workstation player for windows and create ubuntu workstation player using .iso file downloaded from ubuntu official website. Assigned 80 GB memory and 8 virtual CPUs. Enable Nested Virtualization by selecting 'Virtualize Intel VT-x/EPT or AMD-V/RVI' in virtual machine settings.

* Fork the linux repository to your personal github account and clone it using cmd git clone. This clones the linux kernel sources.

* Then edit cmpe283-1.c to add code for proc based, secondary proc based, entry and exit controls. This code interprets and outputs the values that are read from the MSR and tells if the value can be set or cleared. The code has 5 struct defined for each of the control group which is written by referring to Intel SDM. The function report_capability detects and prints VMX capabilities.

* Then go to the linux folder, I had to install gcc(build-essential) , ncurses, pkg-config using sudo apt     install. GCC is GNU Compiler Collection. It is a compiler system mainly used to compile the C and C++ programs. GNU ncurses is software API for controlling writing to the console screen under Unix, Linux and other operating systems.

* Go inside linux directory, make all the modules, install the modules and then reboot using the below commands:
  Make -j 8 modules
  Make -j 8
  Sudo make INSTALL_MOD_STRIP=1 modules_install
  Sudo make install
  Sudo reboot
  
* Add MODULE_LICENSE(“GPL v2”) at the end of cmpe283-1.c file.

* Run make command. After successful build, load and unload module using sudo insmod cmpe283-1.ko and sudo rmmod cmpe283-1.ko. insmod calls function init_module and rmmod calls function cleanup_module.

* Dmesg on cmd prompt to check the VMX features.


* Create cmpe283 directory inside linux and copy Makefile and cmpe283-1.c file to it.

* Finally git add Makefile and cmpe283-1.c, commit and push the changes to linux repo in github.

Kernel is Ready


 ![alt text](https://github.com/limekadabre/linux/blob/master/283output/Kernel_ready.PNG?raw=true)

New linux


 ![alt text](https://github.com/limekadabre/linux/blob/master/283output/linux_new.PNG?raw=true)

Old Linux


  ![alt text](https://github.com/limekadabre/linux/blob/master/283output/linux_old_5.11.PNG?raw=true)


Sudo make install


  ![alt text](https://github.com/limekadabre/linux/blob/master/283output/make_install.PNG?raw=true)
Make


  ![alt text](https://github.com/limekadabre/linux/blob/master/283output/make.PNG?raw=true)



Dmesg : pinbased procbased controls


  ![alt text](https://github.com/limekadabre/linux/blob/master/283output/output1.PNG?raw=true)


Secprocbased


  ![alt text](https://github.com/limekadabre/linux/blob/master/283output/output2.PNG?raw=true)


Entry and exit controls  


 ![alt text](https://github.com/limekadabre/linux/blob/master/283output/output3.PNG?raw=true)


© 2021 GitHub, Inc.
Terms
Privacy
Security
