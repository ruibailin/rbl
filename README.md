# RBL
RTOS Basic Layer
This project's idea comes from rblos.
The purpose is to build up a platform layer up to SOC baremental software or any RTOS/Linux.
Any embedded software based on RBL can be easily ported and tested in windows or Linux envionment.
This project will be managed by git. While RBLOS's version is managed by directory. 

The basic idea of RBL is to avoid name polution when an embedded system is compiled in Linux or Cygwin.
For example:
The embedded system will have its own printf which output char though UART, 
But when compile and run the embedded system on Cygwin, there is another version of printf from Cygwin.
So you really want the printf to output to screen, so you can call rbl_printf which comes from RBL.
RBL is a serious of libaries in which rbl_printf will call the real printf from Cygwin
In that way, you don't need to change the embeded version of printf.

The second idea is to replace all BSP API which to operate with CPU and SOC hardware with software stub function.
The stub function will emulate all hardware behavior.

Why do we need to run embeded software on Cygwin?
It's related to efficiency.
The usally ways to debug are :
1. use simulator and hardware
2. use emulator such as Qemu

Both ways to debug is not convienent as Cygwin's application debug.
