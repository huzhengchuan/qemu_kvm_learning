##QEMU monitor  

QEMU monitor是QEMU与实现用户交互的一种控制台，在该控制台可以使用复杂的命令实现对客户机的操作。


* monitor启动 
  1. 在显示的qemu窗口中，“Ctrl+Alt+2”组合键可以切换到QEMU monitor中，在monitor窗口中输入“Ctrl+Alt+1”可以回到客户机标准显示窗口。
  2. monitor重定向功能:-monitor dev 将monitor重定向到宿主机的dev设备上，dev的取值类型可以有一下几种：
		* vc 虚拟控制台 默认模式，启动窗口
		* /dev/XXX 使用宿主机的终端(tty), /dev/ttyS0 将monitor重定向到宿主机的ttyS0串口上。
		* null 不使用连接到monitor
		* stdio 标准输入输出上，`比较方便的做法`

* 常用命令
	* help命令  `help savevm`
	* info命令 显示当前的状态
		* `info version` 显示QEMU版本
		* `info kvm` 是否支持kvm
		* `info name`
		* `info status` 虚拟机运行状态
		* `info uuid`
		* `info cpus` 客户机各个vcpu信息
		* `info registers` 客户机寄存器状态信息
		* `info tlb` TLB信息，显示客户机虚拟地址到客户机物理地址映射
		* `info mem` 查看正在活动中的虚拟内存页
		* `info numa` 客户机中看到NUMA结构
		* `info mtree` 树状展示内存信息
		* `info balloom` 查看ballooning使用情况
		* `info pci` 查看PCI设备状态信息
		* `info qtree` 树状显示所有客户机中所有设备
		* `info block` 查看块设备的信息
		* `info chardev` 查看字符设备信息  串口 冰块
		* `info network` 查看客户的配置网络信息
		* `info usb` 查看客户机中虚拟USB hub上的usb设备
		* `info usbhost` 查看宿主机中的USB设备信息
		* `info snapshots` 当前系统保存的快照信息
		* `info migrate` 查看当前客户机迁移状态
		* `info roms` 显示客户机使用的BIOS等ROM文件的信息
		* `info vnc` 当前客户机vnc状态
		* `info history` 历史命令执行记录
	* `commit` 提交修改变化到硬盘文件中
	* `cont/stop` 恢复/暂停虚拟机运行
	* `change` 改变设备配置 change vnc localhost:2 
	* `balloon` 改变分配给客户机的内存大小
	* `device_add/device_del` 动态添加或移除设备
	* `mgration`