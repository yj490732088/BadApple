注意：
	1.程序用到了多线程，提示LD错误的话请安装线程库
	2.USB串口的默认路径是 /dev/ttyUSB0
	3.如果提示设备打开失败，重新插拔一次USB串口，使用 demsg 命令来查看最新的USB设备变动，找出你使用的串口设备名字，修改170行的uartname 即可

关于BIN文件的制作：
	1.下载KMPlayer播放器，打开视频后，CTRL+G可以唤出连续截图，将尺寸设为128*64，连续捕获，调整好帧率
	2.安装Tools文件夹内的Image2LCD V3.2 ,设置输出类型为 .bin, 数据水平，字节垂直， 单色， 128*64 字节内像素反序
	3.可以先转换一张图片，生成一个bin文件，通过串口助手发送至STM32试一下效果（注意STM32去掉帧头帧尾检查）
	4.使用批量转换命令，生成一系列的bin文件，如PIC0001.bin~PIC1234.bin
	5.使用CMD命令行进入保存连续截图的文件夹，创建一个空文件：BadApple.bin
	6.使用命令 copy BadApple.bin + PIC****.bin	将所有bin按顺序合成到BadApple.bin当中
	7.放入linux上位机目录内读取发送
	
	8.或者，直接使用Tools文件夹内提供的bin文件，一共6000++张图片，程序内进行了跳1帧处理，不然STM32速度赶不上
	