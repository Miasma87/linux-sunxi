Driver Installation in Linux

1.  Download "v4l-dvb-(version)" source code from http://linuxtv.org/. 

2.	Copy the folder 'rtl2832u_linux_driver' and "v4l-dvb-(version)" source code to the desktop.

3.	Click 'Applications' -> 'Accessories' -> 'Terminal' to enter the console mode. 

4.	Type 'cd /root/Desktop/rtl2832u_linux_driver' to enter the folder.

5.	In the folder 'rtl2832u_linux_driver', type the following command to compile & install. 

	a. Type 'cp -f *.* /root/Desktop/v4l-dvb-(version)/linux/drivers/media/dvb/dvb-usb' to copy all files into v4l-dvb-(version) code.

	b. add the following lines to Makefile in v4l-dvb-(version)/linux/drivers/media/dvb/dvb-usb.
dvb-usb-rtl2832u-objs = demod_rtl2832.o	dvbt_demod_base.o dvbt_nim_base.o foundation.o math_mpi.o nim_rtl2832_mxl5007t.o nim_rtl2832_fc2580.o nim_rtl2832_mt2266.o rtl2832u.o rtl2832u_fe.o rtl2832u_io.o tuner_mxl5007t.o tuner_fc2580.o tuner_mt2266.o tuner_tua9001.o nim_rtl2832_tua9001.o
obj-$(CONFIG_DVB_USB_RTL2832U) += dvb-usb-rtl2832u.o

	c. add the following lines to Kconfig in v4l-dvb-(version)/linux/drivers/media/dvb/dvb-usb.	
config DVB_USB_RTL2832U
	tristate "Realtek RTL2832U DVB-T USB2.0 support"
	depends on DVB_USB
	help
	  Realtek RTL2832U DVB-T driver.
				
   	d. Type 'make clean'
   	d. Type 'make'   	
   	f. Type 'make install'

6.	Plug in our DVB-T USB device;

7.	Type 'lsmod | grep dvb', and it will show
   	dvb_usb_rtl2831u
   	dvb_usb
   	dvb_core
   	i2c_core
    
    Your driver has been installed successfully.

8. Install the applications --'Xine' and 'linuxtv-dvb-apps'. 
