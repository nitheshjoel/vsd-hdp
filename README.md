# VSD-Hardware Design Program

Documentation on SoC Design from Specifications to RTL to GDSII

- [WEEK_0](#WEEK_0)
  - [Introduction_to_Overall_RTL2GDS_Flow](#Introduction_to_Overall_RTL2GDS_Flow)
    	An IP which is Silicon proven holds highest weightage.
    	A sigle chip cycle takes a duration of 14-16 months.
	Out of this, nearly 4 months are taken to process the GDS data to be fabricated on silicon wafer.
	Steps involved to convert to IP Specifications to RTL to GDSII for fabrication:
		Step 1: 
		Consider an Application written in C language, 
		we use GCC (GNU(Gnu's Not Unix) Compiler Collection) to test the application and measure ouput O0.
		Step 2:
		Model the specifications in C-format, and test the application with this model.
		In this particular case, we use RISC-V GCC to compile and test the application and measure O1.
		O0 should be equal to O1.
		![image](https://github.com/user-attachments/assets/2f96dcaa-03bf-477b-8341-3605612ef5f0)
		With these steps we freeze the specifications.
		Step 3:
		Writing softcopy of Hardware.
		Basic using Verilog.
		Industries use advanced platforms like Bluespec, Chisel.
		Again run the same application on this hardware and measure O2.
		O1 should be equal to O2.
		![image](https://github.com/user-attachments/assets/9af4c1b2-0d41-46e1-94a5-d2f3916b2e1a)
		Step 4:
		Dividing Verilog code as:
		Processor (Gate-level IPs need to be synthesizable )
		Peripherals/Ips 
			ANALOG, need not be synthesizable (DAC,ADC,PLL)
			Macros, need to be synthesizable (Ex.: Clock divider circuits)
		![image](https://github.com/user-attachments/assets/b1e69b98-53a2-4129-8699-649889ac53e9)
		Step 5:
		SoC integration using GPIOs.
		The same application is run on this Integarated SoC and ouput O3 is generated.
		Finally, O0=O1=O2=O3
		Step 6:
		Mask Layout design, and generate GDSII(Graphical Data Stream Information Interchange)
		![image](https://github.com/user-attachments/assets/a139cc12-e08d-42cb-a1b3-a4d54547dcc3)
		Additional Info:
		MicroProcessor is part of Microcontroller.
 - [Tools_Installation](#Tools_Installation)
   		System Check
			6GB RAM, 50 GB HDD
			Ubuntu 24
			4vCPU
   
		Tool check

		Yosys
		$ sudo apt-get update
		$ git clone https://github.com/YosysHQ/yosys.git
		$ cd yosys
		$ sudo apt install make (If make is not installed please install it) 
		$ sudo apt-get install build-essential clang bison flex \
   		  libreadline-dev gawk tcl-dev libffi-dev git \
    		  graphviz xdot pkg-config python3 libboost-system-dev \
    		  libboost-python-dev libboost-filesystem-dev zlib1g-dev
		$ make config-gcc
		$ make 
		$ sudo make install
		![image](https://github.com/user-attachments/assets/98ec8f12-1be9-4cd5-8aa6-28556902030b)

		Iverilog
		Steps to install iverilog
		sudo apt-get update
		sudo apt-get install iverilog
		![image](https://github.com/user-attachments/assets/6d44bbbd-7a65-428f-a8fd-39be940e2c95)

		gtkwave
		Steps to install gtkwave
		sudo apt-get update
		sudo apt install gtkwave
		![image](https://github.com/user-attachments/assets/04acf385-0535-4438-bcb5-deb6914f72ca)

		OpenSTA (not needed for SFAL participants)
		https://github.com/The-OpenROAD-Project/OpenSTA
		Not checked yet about OpenSTA

		ngspice
		After downloading the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory, unpack it using:
		$ tar -zxvf ngspice-37.tar.gz
		$ cd ngspice-37
		$ mkdir release
		$ cd release
		$ ../configure  --with-x --with-readline=yes --disable-debug
		$ make
		$ sudo make install
		![image](https://github.com/user-attachments/assets/5b050984-2fe9-4f28-bd2d-aff1acd151e5)

		magic
		$   sudo apt-get install m4
		$   sudo apt-get install tcsh
		$   sudo apt-get install csh
		$   sudo apt-get install libx11-dev
		$   sudo apt-get install tcl-dev tk-dev
		$   sudo apt-get install libcairo2-dev
		$   sudo apt-get install mesa-common-dev libglu1-mesa-dev
		$   sudo apt-get install libncurses-dev
		$   git clone https://github.com/RTimothyEdwards/magic
		$   cd magic
		$   ./configure
		$   make
		$   make install

		OpenLANE-
		sudo apt-get update
		sudo apt-get upgrade
		sudo apt install -y build-essential python3 python3-venv python3-pip make git
		sudo apt install apt-transport-https ca-certificates curl software-properties-common curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
		echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
		sudo apt update
		sudo apt install docker-ce docker-ce-cli containerd.io
		sudo docker run hello-world
		sudo groupadd docker
		sudo usermod -aG docker $USER
		sudo reboot 

   		After reboot
		docker run hello-world

		Check dependencies 
		git –version				git version 2.43.0
		docker –version				Docker version 28.1.1, build 4eba377
		python3 –version			Python 3.12.3
		python3 -m pip –version			pip 24.0 from /usr/lib/python3/dist-packages/pip (python 3.12)
		make –version				GNU Make 4.3
		python3 -m venv -h			

		Below steps installs PDKs and Tools
		cd $HOME
		git clone https://github.com/The-OpenROAD-Project/OpenLane
		cd OpenLane
		make
		make test

- [WEEK_1](#WEEK_1)
