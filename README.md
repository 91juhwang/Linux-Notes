# Linux Notes
Notes and practices to prepare for various Linux certificates like LPI Linux Essentials, LPIC 101 and Redhat RHCSA exam

## Introductory of Linux (LPI Linux Essentials)

### Completed Topics:

#### [Connect to the VNC using Linux Academy CentOS7 server](https://linuxacademy.com/cp/courses/lesson/course/322/lesson/2/completed/1/module/38)

#### [Install CentOS7 w/ Virtual Box](https://linuxacademy.com/cp/courses/lesson/course/322/lesson/2/completed/1/module/38)

#### [Server Applications](https://linuxacademy.com/cp/courses/lesson/course/319/lesson/2/completed/1/module/38)

Network Protocols - mostly use ports to transfer data.

Common Network Ports (Connections for Clients)

 * Port 22 - SSH (Open SSH)

 * Port 23 - Telnet (telnetd)

 * Port 25 - SMTP (Sendmail)

 * Port 53 - DNS (Bind, named)

 * Port 67 - BOOTP (dnsmasq, dhcpd)

 * port 80 - HTTP (Apache)

 * Port 443 - HTTPS (Apache)

#### [Development Languages](https://linuxacademy.com/cp/courses/lesson/course/319/lesson/4/completed/3/module/38)

Software Development Models

* Cathedral Model (Organized, people will see the code once it's released)

* The Bazaar Model (less organized, and relies heavily on developers' contributions)

#### [Package Management Tools and Repositories](https://linuxacademy.com/cp/courses/lesson/course/319/lesson/7/completed/6/module/38)

Each package contains of

* Dependency Information
* Version Information
* Architecture Information
* Binary packages are packages that have an executable from source

Two common package systems are usually used today.

* RPM (Redhat)
* Debian

Debian based package manager uses `apt`

RPM based package manager = `yum`

RPM BASED COMMANDS!!
Yum is tied to repos as RPM is tied to packages

* `rpm -ihv` - install and shows the progress in verbose mode (i,h,v)
* `nano-2.2.6-1.x86_64` - package_name-version-buildNumber.architecture
* `rpm -qi nano` - displays the detail information about the package
* `rpm -e nano` - Remove rpm package
* `yum search apache2` - search package in the yum package manager (apache2 is httpd.x86_64)
* `yum check-update package name` - Check for updates
* `yum deplist httpd.x86_64` - list dependecies

## Useful Commands

* `ls -p` - `-p` flag indicates they are folders.
* `ls -R` - Displays the contents inside a directory
* `halt` - Shuts down the Linux operating system when super user or root user
* `reboot` - Shutdown & Reboot
* `init 0` - Just like Shutdown (halt)
* `init 6` - Just like Reboot
* `su` - switch user
* `top` - lists all the application and processes
* `netstat` - shows the statuses of the network and much more details
* `route` - view a routing table and manipulate routing tables
* `ifconfig` - net configurations, can also modify configuration settings
* `ip addr` - shows ip addresses (only in newer version of Linux)
* `uname` - turns information about Linux
  * `-s` - displays the Linux kernel's name
  * `-n` - displays the host name
  * `-r` - displays the Linux release number
  * `-v` - displays ther version number
  * `-m` - displays the hardware architecture
  * `-p` - displays the processor type
  * `-i` - displays the hardware platform
  * `-o` - displays the OS

## Globbing

* `ls ??.txt` - find two letters.txt files
* `ls *.txt` - find all files that ends with .txt
* `ls [F]*.txt` - search for all txt files that starts with capital `F`
* `ls f[igh][lae]e*.txt` - first letter is f, second character consist of `igh`, third character with [lae], fourth letter of e.

Obviously, don't use wildcards in the file name!

## man

`man -k network` - search anything related to network

## Linux File Systems

* `bin` - consists of executable files
* `boot` - boot related files
* `dev` - various hardware files
* `etc` - text based configuration files and services running
* `lib` - code library for files in the `bin/`
* `mnt` - external drives
* `proc` - Does not exist in our file system, sudo file system that is dynamically created when accessed.


## Commands

*  `grep -in james ./txt2.txt`
* `find . -type f` - can work with directories as well, `-type d`
* `find . -type f | grep file` - find and pipe out the current directory and grep a file that includes `file`
* `cut -d" " -f3 file2.txt | cut -c2` - cut delimeter by space of the field 3 of file2.txt then pipe out and cut column 2
* `wc -w file2.txt | cut -d" " -f1` - only display the counted word, and not the file name

## Input Output Redirection
* `tail /var/log/messages 1> logtemp.txt` - redirecting the output of `/var/log/messages` to a new file called `logtemp.txt`. Output is redirected by using `>`
* `cat wrong_file.txt 2> error.txt` - Redirect the stdError output to the error.txt. This copies the error message to the error.txt, whereas `1>` redirects the correct stdInput to the new file.
* `ps >> runningproccess.txt` - APPEND the output `ps command` to the `runningproccess.txt` file.
  * 1 `>` will replace or create a file, whereas 2 `>>` will append it to the file.

To log the information, we typically do below command to separate the stdinput and stderror
* `mount 1> mountfile.txt 2> mounterror.txt` - Add correct output to mountfile, if error occurs, logs it to mounterrortxt

* `sort < words.txt` - the less than sign, `<` will input. In this case, the contents in the words.txt file will be inputted to the sort command

## Regex

* `[asd]` - matches any in the bracket
* `^music` - matches the beggining of a file that starts with this word
* `music$` - matches end of the file
* `.` - any character
* `grep ^.b abc.txt` - anything that begins with `somethingb`
* `grep ^...$ abc.txt` - grep anything that starts and end with only 3 characters ...
* `ls file*` - will return anything that starts with file. file1, file2, file3 blahblah
* `grep [ser] ./hostnames` - grep files that contains any of the `[ser]`. Will return files with only `er` or `r`.
* `grep [^ser] ./hostnames` - grep files that DOES NOT CONTAIN `[ser]`. Different from outside of bracket `^`

## Scripting

* `if/else` configs
![alt text](https://drive.google.com/uc?id=0Byxeja4jYwq4VWl2YmViS0VfbFE)

* Loops
```shell
for i in `seq15`
  do
    echo "The current number is $i"
  done
exit 0
```