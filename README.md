# Cyber-Trace-A-Lightweight-Breach-Analysis-Framework
Engineered an automated cybersecurity framework using open-source tools for intrusion detection, vulnerability scanning, forensic analysis, and real-time threat mitigation.
J)	Part I: Installation Guide
1.	System Requirements Minimum:
•	OS: Kali 
Tools Required:
•	Suricata (Intrusion Detection System)
•	Tcpdump (Network Traffic Capture)
•	journalctl (System Log Monitor)
•	Nmap & Nikto (Vulnerability Scanners)
•	AVML (Memory Dump Acquisition)
•	Foremost (File Carver & Recovery)
•	hashdeep (File Integrity Checker)
•	GoAccess (Web-based Log Analysis and Dashboard)
2.	Tool Installation & Configuartion
a.	Suricata (IDS Setup):
Command: sudo apt update
Command: sudo apt install -y suricata
Command: sudo suricata -i eth0 -D
b.	tcpdump:
Command: sudo apt install -y tcpdump
Command: sudo tcpdump -i eth0 -w capture.pcap
c.	journalctl (System Log Monitoring):
Available by default in systemd-based systems:
journalctl -xe | grep "authentication"
d.	Dependencies
pip install -r requirements.txt
e.	Nmap & Nikto (Vulnerability Scanners):
sudo apt install -y nmap nikto
nmap -sV target_ip
nikto -h http://target_ip







f.	AVML (Memory Forensics):
wget https://github.com/microsoft/avml/releases/latest/download/avml
chmod +x avml
sudo ./avml memory.lime

g.	Foremost (File Recovery):
sudo apt install -y foremost
sudo foremost -i memory.lime -o recovered_files/

h.	 hashdeep (File Integrity Check):
sudo apt install -y Hashdeep
hashdeep -r /etc > baseline_hashes.txt
hashdeep -r -a -k baseline_hashes.txt /etc

i.	i. Log Dashboard:

sudo apt install -y goaccess

sudo goaccess /var/log/syslog -o /var/www/html/report.html --log-format=SYSLOG --re


Execution Scripts
Place your automation shell scripts inside /opt/cybertrace/scripts/. Example:
Start All Tools (start_monitoring.sh):
#!/bin/bash
suricata -i eth0 -D
tcpdump -i eth0 -w /opt/cybertrace/logs/tcpdump/traffic.pcap &
journalctl -f > /opt/cybertrace/logs/journalctl/syslog.log &
Make executable:
chmod +x start_monitoring.sh
./start_monitoring.s 


]_H
Part II: User Manual
1.	Launch Intrusion Detection
Command: sudo suricata -i eth0 -D
Logs: /var/log/suricata/fast.log

2. Capture Network Traffic
Command: sudo tcpdump -i eth0 -w traffic.pcap
Output: PCAP file for later forensic analysis

3. Perform Vulnerability Scan
Nmap: nmap -sV target_ip
Nikto: nikto -h http://target_ip

4. Memory Dump & Analysis
AVML Dump: ./avml memory.lime
Foremost Recovery: foremost -i memory.lime -o ./recovered_files

5. File Integrity Check
Baseline: hashdeep -r /etc > baseline.txt
Verify: hashdeep -r -a -k baseline.txt /etc

6. View Dashboard
GoAccess Report:
goaccess /var/log/syslog -o /var/www/html/report.html --log-format=SYSLOG --real-time-html
Access via Browser: http://localhost/report.html

🛠 Troubleshooting
•	Suricata not running: Ensure eth0 interface exists and Suricata is not blocked by firewall.
•	tcpdump permission error: Run as sudo
•	AVML issues: Ensure executable permission and kernel supports memory dumping.
•	GoAccess blank page: Confirm syslog path and log format match.
•	hashdeep mismatch: Verify correct baseline hash and unchanged files.

