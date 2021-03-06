# Setting-up-Tiny6410-source-code
Steps to download and set up Tiny6410's source code in Linux

1) Download the files present in the location (If you download teh zip file, have them unzipped)
    https://github.com/VenkatRajaIyer/Setting-up-Tiny6410-source-code/tree/master/mini6410_Samsung-master
    
2) You can copy those packages into /home/$MACHINE_NAME/mini6410/ 
    (If you are using the UI, you don't have to create the folder with your machine name. Simply create the folder mini6410 under home directory)

3) Open the terminal and switch to the super user. You would have to type the administrator's password if prompted
    Type in 'sudo su'
    
3) Extract the downloaded packages into /opt directory. To do that, type in the following commands in th terminal.
    tar -xvzf arm-linux-gcc-4.5.1-v6-vfp-20101103.tgz -C /	<br>
    mkdir /opt/FriendlyARM/mini6410	<br>
    mv /opt/FriendlyARM/toolschain /opt/FriendlyARM/mini6410	<br>
    tar -xvzf linux-2.6.38-20110718.tar.gz -C /opt/FriendlyARM/mini6410/ 	<br>

4) Type in 'gedit ~/.bashrc &' in the terminal
 
5) Add the following before the first line in the file that opens up.
    export PATH=$PATH:/opt/FriendlyARM/mini6410/toolschain/4.5.1/bin
    You might then have to close the terminal and reopen it.
    
5) Go to /home/$MACHINE_NAME/mini6410/mini6410_Samsung-master and type in the follwing	<br>
	cp config.txt /opt/FriendlyARM/mini6410/linux-2.6.38/	<br>
	cd /opt/FriendlyARM/mini6410/linux-2.6.38/	<br>
	mv config.txt .config	<br>	
	sudo apt-get install ncurses-dev	<br>
        make			<br>
	
	If you have installed a 64 bit ubuntu, and as ARM11 is a 32 bit machine, you would have to install some additional libraries
	Type in the following
	sudo apt-get install lib32ncurses5	<br>
	sudo apt-get install lib32z1	<br>
	
6) Type in arm-linux-gcc -v and check if you can see the gcc version to ensure that you have installed the gcc crosscompiler properly

7) Extract the examples files to the linux-2.6.38 folder	<br>
    tar -xvzf /home/$MACHINE_NAME/mini6410/examples-mini6410-20110104.tgz -C /opt/FriendlyARM/mini6410/linux-2.6.38/
    
8) To view the kernel configuration file, navigate to the following location	<br>
    cd /opt/FriendlyARM/mini6410/linux-2.6.38/<br>
    Type in 'make menuconfig'
