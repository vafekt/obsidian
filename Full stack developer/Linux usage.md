1. Basic command structures
- Shell vs bash vs sh
	- **Shell**: A shell is a program that provides an interface for users to interact with the operating system. It interprets commands entered by the user and executes them. It also facilitates communication between the user and the operating system kernel.
	- **Bash (Bourne Again Shell)**: Bash is one specific type of shell, which is an enhanced version of the original Unix shell, known as the Bourne Shell (sh). Bash is the default shell for most Linux distributions and macOS.
	- **sh (Bourne Shell)**: sh, or the Bourne Shell, is one of the earliest Unix shells developed by Stephen Bourne. It is a basic shell that provides fundamental command execution and scripting capabilities. It's often used in shell scripts and as a basic interactive shell.
	- We can check with command: ==echo $SHELL==, or ==which bash==
	- When we run as root, the prompt is #. When not, it displays $
	- Although Bash is a type of shell, there are other shells available as well, such as Korn shell (ksh), C shell (csh), and Z shell (zsh)
- Display the present working directory
	- ==pwd==
- Lists the contents of the current directory
	- ==ls==
	- If we want to show attributes such as: Rules and date of directories and files, use ==ll==
- See the usage of command:
	- ==man []==
	- For example: man ls
- Creating and executing bash scripts
	- These scripts end with ==.sh==
	- Firstly, we need to create file (use nano, vim)
	- Then adding the Shebang (start of the file) to tell the shell to execute it via bash shell:
		- ```#!/bin/bash```
	- Example:
		- ```#!/bin/bash
			echo "Today is " `date`
			echo -e "\nenter the path to directory"
			read the_path
			echo -e "\n you path has the following files and folders: "
			ls $the_path```
	- After that we need to execute the bash script by modifying the ownership of this file (chmod)
	![[Pasted image 20240217221110.png]]
	- Then run the script by using
		- `sh run_all.sh`
		- `bash run_all.sh`
		- `./run_all.sh`
- Variables and data types in Bash
![[Pasted image 20240218004521.png]]
- Gathering input
	- Using the ``read`` command
	![[Pasted image 20240218004649.png]]
- Reading from a file
	![[Pasted image 20240218091736.png]]
- Adding argument
	- Use from ``$1`` to `$...`
	![[Pasted image 20240218092015.png]]
	![[Pasted image 20240218092031.png]]
- Writing to a file
	![[Pasted image 20240218092431.png]]
- Appending to a file
	![[Pasted image 20240218092450.png]]
- Basic Bash commands
	![[Pasted image 20240218092629.png]]
- Conditional statements
	![[Pasted image 20240218093831.png]]
	- ``-gt`` means greater than
- Looping and branching in Bash
	- While loop:
	![[Pasted image 20240218094758.png]]
	- For loop:
	![[Pasted image 20240218094829.png]]
	- Case statements
	![[Pasted image 20240218095230.png]]
2. Files structure
![[Pasted image 20240218100132.png]]
- Root
	- Every single file and directory start from the root directory.
	- The only root user has the right to write under this directory.
- ./bin
	- Essential command binaries that need to be available in single-user mode; for all users, e.g., cat, ls, cp. 
		- Contains binary executables.
		- Common Linux commands you need to use in single-user modes are located under this directory.
		- Commands used by all the users of the system are located here e.g. ps, ls, ping, grep, cp
- ./etc
	- Contains configuration files required by all programs.
	- This also contains startup and shutdown shell scripts used to start/stop individual programs.
	- Example: /etc/resolv.conf, /etc/logrotate.conf.
- ./sbin
	- Essential system binaries, e.g., fsck, init, route
	- The Linux commands located under this directory are used typically by system administrators, for system maintenance purposes
	- Example: iptables, reboot, fdisk, ifconfig, swapon
3. Searching and filtering data
- Find a file in Linux by name or extension
	- ``find /home/username/ -name "*.txt"``
	- Applying grep to find exactly the file
4. Users in Linux
- users refer to individuals or entities that interact with the operating system by logging in and performing various tasks.
- Each user has its own properties
	- username
	- UID (User ID)
	- GID (Group ID)
	- Home directory
	- Default shell
	- Password
- Type of users in Linux
	- System users: created by the system during the installation
	- Regular users: created by the administrator
- Creating users
	![[Pasted image 20240218102733.png]]
	- We can check the ID through command: ```id john```
	- Setting password
		- `sudo passwd john`
	- Assign users to groups in Linux
		- `sudo usermod -aG marketing sarahsmith`
	- Creating new group
		- `sudo groupadd marketing`
5. Resource monitoring
- Displaying the Linux processes
	- `ps -A`
- In Kali, there is a task manager application `top`
	- Killing processes: `kill [process ID]`
6. Network settings
- Steps
	- Setting up the network interfaces
	- Configuring IP addresses
	- Routing and gateway
	- DNS configuration
- In Debian, we can configure in /etc/network/interfaces
	- iface eth0 inet static 
	- address <ip_address> 
	- netmask <network_mask> 
	- gateway <gateway_ip>
	- Or through command `sudo ip addr add 192.168.1.100/24 dev eth0`
- To register DNS server, open /etc/resolv.conf
	- nameserver 8.8.8.8 
	- nameserver 8.8.4.4
- Then we need to restart the networking service or reboot
	- `sudo systemctl restart networking`
- For setting DHCP server, we need to install dhcpd
	- `sudo apt-get install isc-dhcp-server`
	- Configuration
		![[Pasted image 20240218132223.png]]
	- Select interface for DHCP server
		![[Pasted image 20240218132252.png]]
7. Popular tools
- Nslookup
	![[Pasted image 20240218132554.png]]
- Route
	- For checking the route table, or adding or removing route
		- `sudo route add default gw 169.254.0.0`
	- Showing route table in numeric form
		- `route -n`
	- Routing cache information
		- `route -Cn`
		- `ip -4 route`
		- `ip -6 route`
	- Adding route
		- `ip route add 172.10.1.0/24 via 10.0.0.100 dev eth0`
	- Setting the interface up
		- `ip link set dev tun0 up mtu 1500`
- Trace routing
	- `traceroute -4 google.com`
		![[Pasted image 20240218133206.png]]
	- `traceroute -m 10 google.com` for setting maximum of hops (TTL value) to go through
	- `traceroute -g 192.168.43.45 google.com` for specifying the gateway
- ifconfig eth0
8. How to install stuffs on Linux (Linux package management)
- On Linux, software is typically built as a _package_, distributed through _repositories_, and managed on the end-user’s system through _package managers_.
	- Repositories are simply the location where the packages are stored, commonly accessible via the internet.
	- These additional packages are called _dependencies_. A single package can sometimes have hundreds of dependencies. When installing, upgrading, or removing packages, these dependencies may also need to installed, upgraded, and optionally removed.
- A _package manager_ reduces the complexity for the end-user by automating the process of obtaining, installing, upgrading, and removing packages _and their dependencies_.
- Type of package managers
	- dpkg
		- It is a low-level package manager, for installing .deb packages (for Debian). Otherwise .rpm or .dmg for CentOS and MacOS
		- **Kali and Ubuntu are based on Debian, but the target audience is very different**. Kali is designed for security professionals, ethical hackers, and penetration testers. Ubuntu is an everyday operating system with productivity and entertainment apps pre-installed
		- But dpkg cannot install dependencies automatically, but you are too lazy to download other thing. So apt is introduced
	- apt (advanced package tool)
		- `sudo apt update`
		- `sudo apt install [your package]`
		- Or: ``sudo apt install /path/to/package/name.deb``
		- When you want to remove:
			- `sudo apt remove [your package]`
	- When we want to install dependencies for Python, Python has its own package managers called pip
		- `pip3 install -r requirements.txt`
		- From that, we need to have git to do everything with projects