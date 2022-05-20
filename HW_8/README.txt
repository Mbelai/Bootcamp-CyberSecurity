Networking Fundamentals Homework: Rocking your Network!
Your Submission: "It's the End of the Assessment as We Know It, and I Feel Fine"
Guidelines for your Submission:
Provide the following for each phase:
List the steps and commands used to complete the tasks.
List any vulnerabilities discovered.
List any findings associated with a hacker.
Document the mitigation recommendations to protect against the discovered vulnerabilities.
Document the OSI layer where the findings were found.

Phase 1
Summary File 
Determine the IPs for the Hollywood office and run fping against the IP ranges in order to determine which IP is accepting connections: fping 15.199.95.91 15.199.94.91 203.0.113.32 161.35.96.20
Results of fping: 161.35.96.20 is alive, 15.199.95.91 is unreachable, 15.199.94.91 is unreachable, 203.0.113.32 is unreachable
RockStar Corp doesn't want any of their servers, even if they are up, indicating that they are accepting connections. So, IP address 161.35.96.20 would be vulnerable as it accepts connections while the other IP addresses when pinged don’t receive packets. 
The findings are OSI layer 3 the networking layer
Phase 2
Summary File 
Determine which ports are open: You will run a SYN SCAN against the IP accepting connections: sudo nmap -sS 161.35.96.20. The port that is open on this IP is port 22 which is ssh. 
A possible vulnerability is  having an unauthenticated remote attacker gaining network access through port 22 by sshing. 
Miginating this vulnerability by having a secure password to grant access for remote access. 
This would be layer 4 transport layers as we are looking for which ports are open. 
Phase 3
Summary file
RockStar typically uses the same default username and password for most of their servers, so try this first:Username: jimi, Password: hendrix
Try to figure out which port/service would be used for remote system administration, and then using these credentials, attempt to log into the IP that responded to pings from Phase 1 by doing Ssh jimi@161.35.96.20
While logged into the RockStar server from the previous step, determine if something was modified on this system that might affect viewing rollingstone.com within the browser. When you successfully find the configuration file, record the entry that is set to rollingstone.com: Go to the etc directory and cat the hosts file in the hosts file the IP address for rolling stone is 98.137.246.8 rollingstone.com
Terminate your ssh session to the rollingstone server, and use nslookup to determine the real domain of the IP address you found from the previous step.
Note: nslookup is a command line utility that can work in Windows or Linux Systems. It is designed to query Domain Name System records. You can use PowerShell or MacOS/Linux terminal to run nslookup.
To run nslookup, simply enter the following on the command line:
nslookup <IP Address> to find the domain associated to an IP address
Nslookup 98.137.246.8, Domain name for the IP address is  unknown.yahoo.com.
OSI layer that these findings were found is the application layer or layer 7
Phase 4
Summary file
Within the RockStar server that you SSH'd into, and in the same directory as the configuration file from Phase 3, the hacker left a note as to where he stored away some packet captures.
View the file to find where to recover the packet captures : cat packetcaptureinfo.txt
Which gives a url of where the captured packets are, My Captured Packets are Here: https://drive.google.com/file/d/1ic-CFFGrbruloYrWaw3PvT71elTkh3eF/view?usp=sharing
Use Wireshark to analyze this pcap file and determine if there was any suspicious activity that could be attributed to a hacker.
After running http.request.method == "POST", there was only one packet and I opened the HTML Form URL under the HTTP data. I found this message, “Hi Got The Blues Corp!  This is a hacker that works at Rock Star Corp.  Rock Star has left port 22, SSH open if you want to hack in.  For 1 Million Dollars I will provide you with the user and password!”
I ran arp.opcode == 2 to filter ARP and in packet five under the ARP reply I found the message, “[Duplicate IP address detected for 192.168.47.200 (00:0c:29:1d:b3:b1) - also in use by 00:0c:29:0f:71:a3 (frame 4)]”. This could be an ARP poisoning attack. 
For the first vulnerability by securing the ports at the company by limiting the amount of ports that could be used. 
For the 2nd vulnerability some recommendation are ARP tables, network isolation and encryption
These finding are found in OSI layer network layer 
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
