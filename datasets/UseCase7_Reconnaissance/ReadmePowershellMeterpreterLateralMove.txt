README

PILOT CASE

Remote Access Tool (Meterpreter) downloaded and executed by client with no signatures followed by PowerShell
lateral movement. 

Scenario

Payload file name: meterpreterhttp.exe
Attacker: 159.203.64.71
C2= http://159.203.64.71:8080
Malicious download from http://159.203.64.71:90/meterpreterhttp.exe
Victim
Local IP = 192.168.4.37
Hostname = Win732

Please see L00T file for powershell, lateral movement actions
attack concludes listing a directory on a remote computer, copying 
a file and uploading it to C2. 
(Have to elevate to system in order load powershell meterpreter extension)

Payload C2 communication was not encrypted. Purporsely done on HTTP
clear text. 
File extracted: newtextfile.txt

Commands done under powershell

dir
cp
Invoke-Command
Get-Process
Net-view
Net-Share
Type
pwd
