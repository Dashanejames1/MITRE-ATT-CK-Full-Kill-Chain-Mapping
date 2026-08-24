# 🔍 MITRE-ATT-CK-Full-Kill-Chain-Mapping


**Author:** Dashane James  
**Lab Environment:** [e.g. VMware Workstation | Kali Linux | Metasploit | Metasploitable 2]  
**Purpose:** The purpose of this repository is to map everything I studied in the related repositories to ATT&CK. This helps to build the mental model that connects actions to framework tactics.
**Status:** 🟢 Active / 🟡 In Progress / 🔵 Completed

---

## 📋 Overview

[]

---

## 🧪 Lab Environment
| Component | Details |
|---|---|
| Hypervisor | VMware Workstation (Host-Only Network) |
| Attacker Machine | Kali Linux 2026.1 — `192.168.79.129` |
| Target Machine | [Metasploitable] — `192.168.79.130` |
| Network Type | Host-Only (isolated, no internet exposure) |
| Host OS | Windows 11 — ASUS Vivobook 14 |

> ⚠️ **Note:** All activity was performed in a controlled, isolated lab environment against deliberately vulnerable machines. No unauthorized access to live networks was performed.

---

## 🛠️ Tools Used

- **[Metasploit]** — a penetration testing framework that packages known exploits into ready-to-run modules, so you can point one at a vulnerable service and attempt exploitation instead of writing exploit code from scratch.
- **[Metasploitable]** — Acts as a target machine with many intentional vulnerabilities to practice penetration testing, ethical hacking, and securely auditing safely.


---

## 🔬 Tasks / Assessments Performed

###1. [Go to attack.mitre.org]

[This task requests that I navigate to attack.mitre.org, in my web browser.]

# Metasploit commands used
[msfconsole]
[info]
[show options]
[use] 
[run]
[set LHOST]
[set RHOSTS]

<img width="326" height="257" alt="Screenshot 2026-08-19 135220" src="https://github.com/user-attachments/assets/87c81925-6940-422e-802d-a54dc94b66a3" />

Launch Metasploit command 1/2



Output



Findings: 




2. [Nmap scan > Reconnaissance > T1595 Active Scanning]
[The goal of this task was to ]

# Commands used
[search]
[use]
[run]


<img width="505" height="161" alt="image" src="https://github.com/user-attachments/assets/34c5220c-7277-4caa-aaaf-6a6cfbbe7ceb" />

Using search command



Output


Findings



3. FTP exploit > Initial Access > T1190 Exploit Public-facing Application

[The objective of this task is ]

# Commands used
whoami
id
uname -a

<img width="324" height="116" alt="Screenshot 2026-08-23 213334" src="https://github.com/user-attachments/assets/61be98f6-44f8-4465-bebf-80e2f62284c1" />

Results of running whoami,id, uname -a.


Output



Finding: 




4. [Reading /etc/passwd > Discovery > T1087 Account Discovery]
   
[This task is to]


Research Summary




5. [Reading /etc/shadow > Credential Access > T1OO3 OS Credential Dumping]
   
[This task is to]


Research Summary


6. [Write the complete kill chain in ATT&CK Terminology.]
   
[This task is to]


Research Summary




📊 Key Findings Summary
Port/Service	Tool Used	Risk Level	Notes
[e.g. 21/tcp FTP]	[e.g. Nmap]	🔴 Critical	[Notes]
[e.g. 23/tcp Telnet]	[e.g. Wireshark]	🔴 Critical	[Notes]
[e.g. 80/tcp HTTP]	[e.g. Nikto]	🟠 High	[Notes]
[e.g. 3306/tcp MySQL]	[e.g. OpenVAS]	🟠 High	[Notes]
[e.g. 22/tcp SSH]	[e.g. Nmap]	🟡 Medium	[Notes]


Risk Levels: 🔴 Critical | 🟠 High | 🟡 Medium | 🟢 Low

🗺️ MITRE ATT&CK Mapping
Action Performed	ATT&CK Tactic	Technique ID	Technique Name
[e.g. Port scanning]	[e.g. Reconnaissance]	[e.g. T1595]	[e.g. Active Scanning]
[Action]	[Tactic]	[ID]	[Technique]
[Action]	[Tactic]	[ID]	[Technique]
[Action]	[Tactic]	[ID]	[Technique]
🛡️ Defensive Recommendations
Based on findings, the following remediations would be recommended in a real environment:

[Finding 1] — [Recommendation]
[Finding 2] — [Recommendation]
[Finding 3] — [Recommendation]
[Finding 4] — [Recommendation]
[Finding 5] — [Recommendation]
📚 CySA+ Exam Relevance
This lab directly maps to the following CompTIA CySA+ (CS0-003) exam domains:

Domain	Coverage
Security Operations (33%)	[What this lab covers in this domain]
Vulnerability Management (30%)	[What this lab covers in this domain]
Incident Response (20%)	[What this lab covers in this domain]
Reporting & Communication (17%)	[What this lab covers in this domain]
🔑 Technical Notes
[Any important notes about your lab setup, workarounds, or lessons learned. Example:

Enumeration


# Any important commands or workarounds
[command here]
shell 

📌 About This Project
[1-2 sentences about how this fits into your overall portfolio and career goals.]

Related repositories:

[Repo Name] — [Brief description]
[Repo Name] — [Brief description]
[Repo Name] — Coming soon
👤 Author
Dashane James
Senior Field Service Technician → Cybersecurity Analyst
📍 Yonkers, NY
🎓 B.S. Information Technology — SUNY Canton
🏆 CompTIA Security+ | CySA+ (In Progress)
🔗 GitHub | Zero Trust Cyber Security Brand

This repository is part of an active portfolio demonstrating hands-on cybersecurity skills. All lab work performed in isolated environments for educational purposes.
