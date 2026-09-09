# 🔍 MITRE-ATT-CK-Full-Kill-Chain-Mapping


**Author:** Dashane James  
**Lab Environment:** [e.g. VMware Workstation | Kali Linux | Metasploit | Metasploitable 2]  
**Purpose:** Map all tasks for the previous related repositories to ATT&CK. This helps to build the mental model that connects attacker actions to framework tactics.
**Status:** 🟢 Active / 🟡 In Progress / 🔵 Completed

---

## 📋 Overview

[The goal for this repository is to demonstrate the MITRE ATT&CK framework and how it is used to map specific vulnerabilities to an exploit.  ]

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

attack.mitre.org 

- **[Metasploit]** — a penetration testing framework that packages known exploits into ready-to-run modules, so you can point one at a vulnerable service and attempt exploitation instead of writing exploit code from scratch.
- **[Metasploitable]** — Acts as a target machine with many intentional vulnerabilities to practice penetration testing, ethical hacking, and securely auditing safely.


---

## 🔬 Tasks / Assessments Performed

###1. [Go to attack.mitre.org]

This task requests that I navigate to attack.mitre.org, in my web browser.

<img width="959" height="412" alt="Screenshot 2026-08-27 145618" src="https://github.com/user-attachments/assets/449beec7-0e3a-4535-b851-7458bd0ea5af" />

attack.mitre.org website screenshot 1/2

<img width="949" height="411" alt="Screenshot 2026-08-27 145649" src="https://github.com/user-attachments/assets/9f13ca79-1301-43a8-a414-ee814d7f73a9" />

attack.mitre.org website screenshot 2/2


Output
After accessing the attack.mitre.org web page it obviously brought me to the MITRE ATT&CK web page which is used by many analysts as a knowledge base of adversary tactics and techniques based on real-world observations. The ATT&CK knowledge base is used around the CS industry as a reference point for building threat models and detection strategies.

Findings: 

The webpage specifically lists tactics, techniques, and defenses of known cyber threats. 

The first page of attack.mitre.org, displays the ATT&CK Matrix for enterprise which includes reconnaissance, resource development, initial access, execution, persistence, privilege escalation, defense evasion, credential access, discovery, lateral movement, collection, command and control, exfiltration, and impact. All of these categories also have more defined subcategories. 


2. [Nmap scan > Reconnaissance > T1595 Active Scanning]
[The goal of this task was to map the Nmap reconnaissance scan to its correct MITRE ATT&CK tactic and technique. Also to understand why version scanning specifically falls under Active Scanning rather than another reconnaissance method.]


(STEP 1: Describe the action in plain english) :
STEP 2:  Identify the tactic/goal
STEP 3: Find the technique within the section of the specified tactic/goal
STEP 4: Check for a sub-technique
STEP 5: Verify

Output

Reconnaissance > T1595.002(Active scanning: Vulnerability Scanning)

Findings

This task falls under reconnaissance because nothing was exploited. The Nmap -sV scan only gathered information about what was running on the target, without accessing or altering anything. 

It's active scanning (T1595) specifically because packets were sent directly to the host, rather than passively observing existing traffic. 

The .002 sub-technique (Vulnerability Scanning) applies because the scan's actual goal was identifying an exploitable software version (vsftpd 2.3.4), not just enumerating which ports were open, which separates .002 from the parent technique.

** mapping template = reasoning > technique reasoning > sub-technique reasoning **

3. FTP exploit > Initial Access > T1190 Exploit Public-facing Application

[The goal of this task was to map the vsftpd 2.3.4 backdoor exploit to it's correct MITRE ATT&CK tactic and technique and understand why gaining shell access through this specific vulnerability qualifies as initial access rather than another tactic.]

Output

Initial Access > T1190 (Exploit Public-facing Application)



Finding: 

This action falls under initial access because it represents the exact moment the attacker gained access they didn't have before. (From no access > a working shell)

This exploit maps specifically to T1190 because FTP was a service exposed to the network, and access came from exploiting a vulnerability in that services' software directly rather than another technique like stolen credentials, phishing, or physical access. 



4. [Reading /etc/passwd > Discovery > T1087 Account Discovery]
   
[This task was to map reading /etc/passwd to its correct MITRE ATT&CK tactic and technique, and understand why enumerating local accounts specifically falls under Account discovery.]


Output 

Discovery > T1087.001


Findings:

Tactic: reading the /etc/passwd file identifies as discovery because the attacker was only learning about the environment and not stealing or altering any information. 

Technique: It maps to T1087 (Account Discovery) because the specific goal was enumerating user accounts, not general system specs (like T1082) or confirming identity (T1033) ???

Sub-technique: .001 (Local Account) applies because /etc/password lists accounts on the local Linux machine itself, not a domain, cloud service, or email system, which are linked to other T1087 sub-techniques. 





5. [Reading /etc/shadow > Credential Access > T1OO3 OS Credential Dumping]
   
[This task is to map reading /etc/shadow to it's correct MITRE ATT&CK tactic and technique, and understand why this action crosses over from discovery and into credential access.]


Output 

Credential Access > T1003.008 (OS Credential Dumping: etc/passwd and /etc/shadow)

Findings:

Tactic: Falls under Credential Access, not discovery because the goal changed from learning/observing the system over to attempting to obtain the password hashes needed to escalate or move elsewhere. 

Technique: Maps to T1003 (OS Credential Dumping) because /etc/shadow stores the actual hash passwords for every local account, and reading this file is a direct attempt to obtain those credentials.

Sub-technique: .008 applies because it specifically covers dumping credentials from Linux's /etc/passwd and /etc/shadow file rather than pulling hashes from memory or a different OS's credential store, which are separate T1003 sub-techniques.  


6. [Write the complete kill chain in ATT&CK Terminology.]
   
[This goal of this task was to break down every stage of this assessment (reconnaissance through credential access.) into one connected kill chain using correct ATT&CK terminology. This shows exactly how each stage's outcome influences the next.]

Output

Stage	Action	Tactic	Technique	Why
1	Nmap -sV scan >	Reconnaissance	> T1595.002 >	Gathering info before attacking; ".002" because it targeted a specific vulnerable version, not just open ports

2	vsftpd backdoor exploited >	Initial Access >	T1190	> First foothold gained; exploited a network-exposed service's software

3	whoami/id, uname -a, cat /etc/passwd >	Discovery >	T1033, T1082, T1087.001 >	Same goal (learn the environment) across all three, but each pulls a different category of info — identity, system specs, accounts

4	cat /etc/shadow >	Credential Access >	T1003.008 >	Goal shifted from "learn" to "obtain credentials"; ".008" is the Linux-file-specific variant

Findings 


Each stage's output became the next stages input. For example, Recon told the attacker what was vulnerable then, that vulnerability became the door for initial access. Next, having a shell, discovery answered "what's here", knowing accounts existed, credential access then went after the passwords protecting them. That chain "of "this enabled that" is what makes it a kill chain rather than four unrelated events.

The outline for MITRE ATT&CK's own structure is Tactic > Technique > Sub-Technique



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

The outline for MITRE ATT&CK's own structure is Tactic > Technique > Sub-Technique

(STEP 1: Describe the action in plain english) :
STEP 2:  Identify the tactic/goal
STEP 3: Find the technique within the section of the specified tactic/goal
STEP 4: Check for a sub-technique
STEP 5: Verify


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
