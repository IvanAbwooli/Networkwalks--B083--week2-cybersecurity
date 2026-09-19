Penetration Testing Report — Footprinting & Network Scanning
W2-PM-FINAL | Cybersecurity | Networkwalks

 Assessment Information
Field	Details
Program / Batch	B082-Networkwalks
Date	18 August 2026
Modules Completed	W2-PM1 — Multiple Kali Tools
W2-PM5 — Zenmap Scanning
Client / Target	Networkwalks — secured written permission
My own local LAN network
Permission Secured	Yes
Phases Covered	Phase 1: Reconnaissance & Footprinting
Phase 2: Scanning & Network Discovery
Phases 3–5: In Progress
1. Liability Disclaimer
I have performed these activities only on systems and devices where I had secured written permission or on systems/devices that I own myself.

All materials are provided for educational and research purposes only. Unauthorized access or misuse of these techniques may violate applicable laws and regulations.

The instructor, authors, and Networkwalks are not responsible for misuse of the information contained in this report. All actions performed using these techniques remain the responsibility of the individual conducting them.

2. Introduction
This report covers footprinting and reconnaissance of the networkwalks.com domain using multiple Kali Linux tools (W2-PM1) and network scanning of my own local network using Zenmap (W2-PM5).

The two modules demonstrate how security assessment activities can progress from gathering publicly available information to identifying live hosts within an authorized network.

This work forms part of Week 2 of my ongoing internship program at Networkwalks.

All commands were executed in Kali Linux for footprinting activities and on a Windows PC running Zenmap for network scanning.

Each activity was documented with the command used, the observed result, and its relevance to security assessment.

3. Tools Used
Tool	Purpose
Kali Linux & Windows	Operating systems used for reconnaissance and scanning activities
WHOIS	Finding publicly available domain registration information, dates, and name servers
WhatWeb	Fingerprinting web technologies such as servers, CMS platforms, and plugins
nslookup	Resolving domain names to IP addresses through DNS
curl -I	Inspecting HTTP response headers
WAFW00F	Detecting the presence of Web Application Firewalls
DNSRecon	Enumerating DNS records including NS, MX, SPF, TXT, and SRV records
Zenmap (Nmap GUI)	Discovering live hosts and identifying IP/MAC addresses on the authorized local subnet
Windows CMD	Local IP and MAC address identification
 4. Activities Performed
4.1 Footprinting & Reconnaissance
I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools:

WHOIS

WhatWeb

nslookup

curl

WAFW00F

DNSRecon

Each tool was used to collect a different category of information.

WHOIS
WHOIS was used to obtain publicly available domain registration information and identify the domain's name servers.

The results provided information relating to the domain registration and hosting infrastructure.

WhatWeb
WhatWeb was used to identify technologies associated with the website.

The observed results identified:

WordPress 7.0.4

WP Download Manager 3.3.58

nslookup
nslookup was used to resolve the domain name to its IP address.

The observed result identified:

192.232.216.135
curl
The curl -I command was used to inspect HTTP response headers.

The observed response exposed the WordPress REST API endpoint:

/wp-json/
WAFW00F
WAFW00F was used to determine whether a Web Application Firewall was protecting the website.

The observed result identified:

ModSecurity (SpiderLabs)
DNSRecon
DNSRecon was used to enumerate DNS records.

The results provided information relating to:

Name servers

Mail servers

SPF records

TXT records

4.2 Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my authorized local subnet:

10.32.147.0/24
The scan was performed using:

nmap -sn 10.32.147.0/24
The scan was used to identify live hosts and, where available, their corresponding MAC addresses.

 Discovered Live Hosts & Physical Addresses
#	Host IP Address	MAC Address
1	10.32.147.147	B2:5E:E7:28:B7:7A
2	10.32.147.149	CC:3D:82:DC:83:C2
3	10.32.147.152	7E:BC:E9:E6:B0:34
4	10.32.147.163	6A:63:31:46:0F:24
5	10.32.147.171	4C:D5:77:F3:7D:83
6	10.32.147.177	Not available / Local interface
7	10.32.147.181	C6:47:D6:C3:79:BB
8	10.32.147.182	38:6A:77:52:8E:0D
9	10.32.147.184	C0:18:85:C6:79:F1
10	10.32.147.198	BC:CD:99:0B:6F:94
11	10.32.147.221	8A:1B:2E:D8:DA:B8
12	10.32.147.241	0A:CE:2A:A1:02:F2
Note: The source material states that the scan discovered 10 active hosts, but the supplied host table contains 12 IP addresses. The table above preserves all entries provided in the report.

5. Risk Analysis / Impact
#	Risk / Finding	Evidence	Potential Impact	Risk Level
1	Web technology exposure	WordPress / WP Download Manager versions identified	Attackers may identify software requiring security review	🟠 Medium
2	Server IP identifiable	nslookup resolved to 192.232.216.135	Provides the network location of the web service	🟢 Low
3	HTTP technical information exposed	curl returned /wp-json/	Assists with technology fingerprinting and enumeration	🟢 Low
4	WAF technology identifiable	ModSecurity detected	Reveals security architecture details	🟢 Low
5	DNS information exposed	DNSRecon identified MX/SPF records	Helps build a broader infrastructure profile	🟠 Medium
6	Live hosts visible	Zenmap identified multiple live hosts	Unauthorized devices may be present on the network	🟠 Medium
Risk Level Key
🔴 Critical

🟠 Medium

🟢 Low

6. Recommendations
1. Review Technology Exposure
Regularly audit what CMS and plugin information is publicly visible.

2. Maintain Updates
Keep WordPress, plugins, and other web technologies updated against current security advisories.

3. Harden HTTP Headers
Review HTTP response headers and remove unnecessary technical identifiers where appropriate.

4. Audit DNS Records
Ensure that only necessary DNS records and information are publicly exposed.

5. Tune WAF Configuration
Continue using ModSecurity while reviewing its configuration and security-signature exposure.

6. Perform Regular Network Discovery
Conduct periodic authorized scans of internal subnets to maintain an accurate asset inventory.

7. Investigate Unknown Devices
Verify devices discovered during network scans against an authorized asset inventory.

8. Maintain Documentation
Regularly update network topology diagrams and device inventories.

9. Maintain Authorization
Always obtain explicit written authorization before performing security testing against systems that you do not own.

 7. Conclusion
During Week 2 of the internship, I completed practical activities covering footprinting, reconnaissance, and network scanning.

The exercises demonstrated that information gathering is an important part of security assessment. I gained practical experience using multiple reconnaissance tools in Kali Linux and using Zenmap to identify hosts on an authorized local network.

The activities also reinforced the importance of proper documentation, technical analysis, asset visibility, and authorization when conducting cybersecurity assessments.

📸 8. Evidence
The folder contains the evidence with screenshots