# Vulnerability Management Program Implementation

This project simulates the end-to-end implementation of a comprehensive vulnerability management program, guiding the organization from an initial state of no existing policies or practices to a fully operational and mature process.

_**Initial State:**_ The organization lacks a formal vulnerability management policy and has no established procedures in place.

_**Final State:**_ A formal policy is developed and adopted, stakeholder alignment is achieved, and a complete cycle of organization-wide vulnerability identification, assessment, and remediation is successfully executed.


---

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/cfc5dbcf-3fcb-4a71-9c13-2a49f8bab3e6">

# Technology Utilized
- Tenable (enterprise vulnerability management platform)
- Azure Virtual Machines (Nessus scan engine + scan targets)
- PowerShell & BASH (remediation scripts)

---


# Table of Contents

- [Vulnerability Management Policy Draft Creation](#vulnerability-management-policy-draft-creation)
- [Mock Meeting: Policy Buy-In (Stakeholders)](#step-2-mock-meeting-policy-buy-in-stakeholders)
- [Policy Finalization and Senior Leadership Sign-Off](#step-3-policy-finalization-and-senior-leadership-sign-off)
- [Mock Meeting: Initial Scan Permission (Server Team)](#step-4-mock-meeting-initial-scan-permission-server-team)
- [Initial Scan of Server Team Assets](#step-5-initial-scan-of-server-team-assets)
- [Vulnerability Assessment and Prioritization](#step-6-vulnerability-assessment-and-prioritization)
- [Remediation Round 1: Outdated Wireshark Removal](#remediation-round-1-outdated-wireshark-removal)
- [Remediation Round 2: Insecure Protocols & Ciphers](#remediation-round-2-insecure-protocols--ciphers)
- [Remediation Round 3: Guest Account Group Membership](#remediation-round-3-guest-account-group-membership)
- [Remediation Round 4: Windows OS Updates](#remediation-round-4-windows-os-updates)
- [First Cycle Remediation Effort Summary](#first-cycle-remediation-effort-summary)

---

### Step 1) Vulnerability Management Policy Draft Creation

This phase centers on developing an initial draft of the Vulnerability Management Policy to initiate stakeholder engagement. The draft defines the policy’s scope, assigns roles and responsibilities, and establishes remediation timelines. It serves as a foundational document that is refined through feedback from key departments to ensure feasibility and alignment with operational needs before being finalized and approved by executive leadership.
  
[Draft Policy](https://docs.google.com/document/d/1fcSLMi8IxRXK2qVjd7zO94hvY71rS4hBZOhAFmTuBL4/edit?usp=sharing)

---

### Step 2: Mock Meeting – Policy Buy-In (Stakeholders)


### Executive Summary of Meeting: Vulnerability Management Policy Discussion
 
**Attendees:**  Vulnerability Management and Server Infrastructure Teams
**Subject:** Review and Adjustment of Vulnerability Management Policy Draft

In this phase, a brief and productive meeting was held with the server team to introduce and review the draft of the Vulnerability Management Policy. The draft was generally well-received; however, concerns were raised about the feasibility of meeting the proposed remediation timelines—particularly the 48-hour window for addressing critical vulnerabilities—due to current staffing constraints.

To address this, it was agreed that the critical vulnerability remediation timeline would be extended to one week for most cases, with the 48-hour requirement reserved for urgent scenarios such as zero-day vulnerabilities. Additionally, a request for initial flexibility was made to support teams as they adapt to the new remediation and patching processes.

It was confirmed that following final approval of the policy, a formal rollout will begin, with a 6-month transition period allotted for departments to fully integrate and operationalize the new procedures. This phased approach was welcomed, and the inclusive, collaborative decision-making process was positively acknowledged.

#### Key Takeaways:
- Critical remediation timeline adjusted from 48 hours to 1 week, with exceptions for severe threats.  
- A 6-month grace period will be provided post-policy approval to allow teams to adjust.  
- Strong emphasis on collaboration and shared accountability for implementation success.


---

### Step 3) Policy Finalization and Senior Leadership Sign-Off

After gathering feedback from the server team, the policy is revised, addressing aggressive remediation timelines. With final approval from upper management, the policy now guides the program, ensuring compliance and reference for pushback resolution.  
[Finalized Policy](https://docs.google.com/document/d/1pARIctrh00TuRKwOVR_FcXKBQDLI-p62WmdhrAm-60E/edit?usp=sharing)


---

### Step 4) Mock Meeting: Initial Scan Permission (Server Team)


### Executive Summary of Meeting: Initiation of Credentialed Vulnerability Scans
  
**Attendees:** Vulnerability Management and Server Infrastructure Teams  
**Subject:** Planning for Scheduled Credentialed Scans

This meeting focused on launching credentialed vulnerability scans following the rollout of the Vulnerability Management Policy. Weekly scans are planned for approximately 200 servers, with each scan estimated to take 4–6 hours.

Concerns were raised regarding system performance and the security of granting administrative access. The scanning team clarified that credentials are necessary to inspect registries, detect outdated software, and identify insecure protocols. To address concerns, both teams agreed on a phased approach:

- A single-server test scan will be conducted to monitor resource usage.  
- Temporary Active Directory credentials will be used, enabled only during scan windows and disabled immediately afterward—aligning with a just-in-time access model.

Next steps include automating the temporary credential setup. Full-scale scanning will proceed based on the success of the test scan.

#### Key Takeaways:
- Weekly credentialed scans planned for ~200 servers; each lasting 4–6 hours.  
- Test scan on one server to validate system impact.  
- Temporary credentials will ensure secure, limited scan access.  
- Automation of account provisioning is in progress.


---

### Step 5) Initial Scan of Server Team Assets

In this phase, a Windows Server is intentionally configured with security vulnerabilities to simulate the server team's environment. An authenticated vulnerability scan is then conducted, and the results are exported to support subsequent remediation efforts.  

<img width="1270" height="1102" alt="image" src="https://github.com/user-attachments/assets/53018391-460e-42ac-9957-1a9a5d291797" />


---

### Step 6) Vulnerability Assessment and Prioritization

Based on the chart below, we assessed identified vulnerabilities and developed a remediation prioritization strategy focused on ease of remediation and potential impact. The following priorities were established:

<img width="1304" height="1086" alt="image" src="https://github.com/user-attachments/assets/25e9c2f7-d9e0-4e75-b7ef-18bed8833a3d" />

1. Third Party Software Removal (Wireshark)
2. Windows OS Secure Configuration (Protocols & Ciphers)
3. Windows OS Secure Configuration (Guest Account Group Membership)
4. Windows OS Updates


---

### Step 7) Remediation Effort

#### Remediation Round 1: Outdated Wireshark Removal

A PowerShell script was utilized to remove the outdated installation of Wireshark. A subsequent scan verified that the vulnerability had been successfully remediated.
  
[Wireshark Removal Script](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/remediation-wireshark-uninstall.ps1)  
<img width="1268" height="942" alt="image" src="https://github.com/user-attachments/assets/d534f453-757b-48b7-8472-a111edac466f" />


#### Remediation Round 2: Insecure Protocols & Ciphers

PowerShell scripts were used to remediate insecure protocols and cipher suites. A follow-up scan confirmed successful remediation, and the results were documented and saved for future reference.
 
[PowerShell: Insecure Protocols Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-protocols.ps1)
[PowerShell: Insecure Ciphers Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-cipher-suites.ps1)
<img width="1260" height="704" alt="image" src="https://github.com/user-attachments/assets/a4562899-805a-4b05-a862-9a91e802053a" />


#### Remediation Round 3: Guest Account Group Membership

The guest account was removed from the local Administrators group. A subsequent scan verified successful remediation, and the results were exported for comparison and documentation purposes.

[PowerShell: Guest Account Group Membership Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-guest-local-administrators.ps1)  

<img width="1254" height="640" alt="image" src="https://github.com/user-attachments/assets/c1d14503-46f4-40a2-8203-0f431eb62f7a" />


#### Remediation Round 4: Windows OS Updates

Windows Update was re-enabled, and all pending updates were applied until the system reached full compliance. A final scan confirmed that the updates were successfully implemented.

<img width="1254" height="640" alt="image" src="https://github.com/user-attachments/assets/71c10629-3d53-4676-a5a0-4bd352e08ac7" />



---

### First Cycle Remediation Effort Summary

The remediation process resulted in an 80% overall reduction in vulnerabilities, decreasing from 30 to 6. All critical vulnerabilities (100%) were resolved by the second scan, while high-severity issues were reduced by 90% and medium-severity vulnerabilities by 76%. In a real-world production environment, remediation efforts would be further prioritized based on asset criticality to optimize risk reduction.
 
<img width="2130" height="1320" alt="image" src="https://github.com/user-attachments/assets/628dbbe4-1270-4217-ab4c-e517af4211cc" />


---

### On-going Vulnerability Management (Maintenance Mode)

After completing the initial remediation cycle, the vulnerability management program enters **Maintenance Mode**—a phase focused on sustaining proactive vulnerability oversight to ensure long-term system security. This stage emphasizes regular scanning, continuous monitoring, and timely remediation to maintain a strong security posture.  
(See [Finalized Policy](https://docs.google.com/document/d/1pARIctrh00TuRKwOVR_FcXKBQDLI-p62WmdhrAm-60E/edit?usp=sharing) for scanning and remediation cadence requirements.)

#### Key Activities in Maintenance Mode:
- **Scheduled Vulnerability Scans**: Conduct recurring scans (e.g., weekly or monthly) to identify new vulnerabilities introduced by system changes.
- **Patch Management**: Apply security patches and updates regularly to ensure critical vulnerabilities are promptly addressed.
- **Remediation Follow-ups**: Triage and resolve newly detected vulnerabilities based on risk severity and business impact.
- **Policy Review and Updates**: Reassess the Vulnerability Management Policy periodically to reflect evolving best practices and organizational priorities.
- **Audit and Compliance**: Perform internal audits to confirm adherence to the policy and compliance with applicable regulatory requirements.
- **Stakeholder Communication**: Facilitate ongoing collaboration with remediation teams to support timely and coordinated responses.

Maintaining an active and structured vulnerability management process in this phase helps organizations stay ahead of emerging threats and reinforces long-term resilience in their security operations.

