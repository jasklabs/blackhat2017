README Spearphishing with password protected zip file containing malware exe, password in email body

Attacker Email: rod.soto@jask.io
Victim Email: victim@miamip0wnmachine.com
Mail Client: Thunderbird
Phishing URI: http://bit.ly/2om4gv1
Victim IP: 192.168.4.38
Victim Hostname: WIN764PRO
Lateral Movement Machine IP: 192.168.4.107
Lateral Movement Hostname: Win10ent
Attacker IP: 159.203.64.71
EK URI: http://159.203.64.71:3000/demos/basic.html
Malicious file redirect URI: http://159.203.64.71:90/badfile.zip
C2 URI: http://159.203.64.71:8080
Bad file: badfile.zip --> 64meterpreterhttp.exe (Password 1234)
File copied= machinelearning.pdf
Remote share listed: \\win10ent\share1
Lateral movement entirely done via Powershell 
Payload used windows/x64/meterpreter/reverse_http (CLEAR TEXT HTTP)

Scenario 

V. Tim receives an email from Rod.Soto@jask.io the phishing email says
check this out, password 1234. Email contains a bit.ly uri shortener http://bit.ly/2om4gv1
Vic Tim clicks on URI and goes to EK URI: 159.203.64.71:3000/demos/basic.html
from there Vic Tim gets redirected to http://159.203.64.71:90/badfile.zip 
and prompted for download. Vic Tim opens file and inputs password, executing payload
(windows/x64/meterpreter/reverse_http) connecting back to C2 159.203.64.71:8080.
Attacker then proceeds to move laterally (See LOOT for detail commands). 

Approximate time of actions

- 1:15 EST Vic Tim clicks on link
- 1:16 EST Redirect to http://159.203.64.71:90/badfile.zip 
- 1:17 EST Victim opens file
- 1:18 EST Connect back to C2 159.203.64.71:8080
- 1:19 EST --> Load powershell --> execute powershell_shell
- 1:20 EST arp -a --> attacker gets list of ips 
- 1:20 EST ping -a 192.168.4.107 --> returns hostname of computer win10ent
- 1:21 EST WinRM command check --> Test-WSMan on win10ent (See L00T for specific command)
- 1:23 EST Remote Dir listing of shares via Powershell (Get-WmiObject --> see LOOT file for specific command)
- 1:31 EST Remote content listing of \\win10ent\share1 (Invoke-Command ... --> see L00T file for specific command)
- 1:36 EST Copied machinelearning.pdf from \\win10ent\share1 (10MB)
- 1:37 EST Initiated exfil of machinelearning.pdf file 
