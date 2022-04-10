# Basic-Port-Scanner-with-Python-using-NMAP
Created a basic port scanner with python utilizing nmap - credit given to udemy course "Python for Penetration Testers"

#Steps to create a basic port scanner with nmap and python in Visual Studio Code

1. Install python on device, in this case I used a Windows 10 operating system. 
2. Ensure nmap is installed by running a python shell and typing "import nmap" - if an error pops up it is not installed. In order to install nmap for python launch:

C:\Windows\system32>python
Python 3.10.4 (tags/v3.10.4:9d38120, Mar 23 2022, 23:13:41) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import nmap
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'nmap'

#Here we see that nmap is not installed and received an error.
#Next we will run the command to install python-nmap for this script.
  
C:\Windows\system32>pip3 install python-nmap
Collecting python-nmap
  Downloading python-nmap-0.7.1.tar.gz (44 kB)
     ---------------------------------------- 44.4/44.4 KB 2.1 MB/s eta 0:00:00
  Preparing metadata (setup.py) ... done
Using legacy 'setup.py install' for python-nmap, since package 'wheel' is not installed.
Installing collected packages: python-nmap
  Running setup.py install for python-nmap ... done
Successfully installed python-nmap-0.7.1
  
#You should receive this message if the package successfully installs on your os.
- To successfully continue you need both the nmap scanner and python library downloaded.
  
3. The code listed below for the nmap script.

******************* 
  
import nmap
import sys

target = str(sys.argv[1])
ports = [21,22,80,139,443,8080]

scan_v = nmap.PortScanner()

print("\nScanning", target,"for ports 21,22,80,139,443, and 8080...\n")

for port in ports:
    portscan = scan_v.scan(target,str(port))
    print("Port", port, " is ", portscan['scan'][target]['tcp'][port]['state'])

print("\nHost", target," is ", portscan['scan'][target]['status']['state'])
  
******************* 
  
#This specific script targets ports 21, 22, 80, 139, 443, and 8080.
  
4. Listed below is the command from the scan being successful.
  
 C:\Users\user\Desktop>python nmapscanner.py 127.0.0.1

Scanning 127.0.0.1 for ports 21,22,80,139,443, and 8080...

Port 21  is  closed
Port 22  is  closed
Port 80  is  closed
Port 139  is  closed
Port 443  is  closed
Port 8080  is  closed

Host 127.0.0.1  is  up
