# 🛡️ EDR Home Lab

## 📖 Executive Summary
This project simulated a real-world cyberattack scenario to test **Endpoint Detection & Response (EDR)** capabilities. I deployed **LimaCharlie EDR** on a Windows 10 endpoint, acted as the adversary using **Sliver C2** (Command & Control) to compromise the machine, and performed incident response to identify the threat.

**Role:** Security Analyst / Detection Engineer
**Tools:** LimaCharlie, Sliver C2, Kali Linux, Windows 10, VirtualBox.

---

## 🏗️ Lab Architecture
* **Attacker Node:** Kali Linux (Sliver C2 Server) - IP: `10.68.167.225`
* **Victim Node:** Windows 10 Pro (Endpoint) - IP: `10.68.167.38`
* **Telemetry:** LimaCharlie EDR sensor installed on the victim.
* **Network:** Bridged Adapter configuration to simulate a local LAN compromise.

---

## ⚔️ Phase 1: The Attack (Red Team)
### I generated a custom C2 payload using the Sliver framework. Upon execution by the victim, a persistent C2 session was established, granting me remote shell access.

<img width="857" height="390" alt="image" src="https://github.com/user-attachments/assets/d45454ec-fb8d-48ad-8296-28673e772d0e" />


---

## 🛡️ Phase 2: Detection & Response (Blue Team)

### **1. Sensor Deployment**
 I installed the LimaCharlie EDR sensor on the victim endpoint to establish real-time telemetry.

<img width="841" height="481" alt="image" src="https://github.com/user-attachments/assets/d40b60c2-0ab2-49a0-90a8-26b5147f74d6" />


##  **2. Threat Hunting (Network Telemetry)**
I investigated the process tree and identified `payload (3).exe` (PID 10228). The "Smoking Gun" was the network connection to the attacker IP on Port 8888, confirming a C2 beacon.

<img width="901" height="282" alt="image" src="https://github.com/user-attachments/assets/c42458b2-981c-44b4-bc9c-13eb072e65e0" />


## **3. Incident Response**
I executed a containment action directly via the EDR console to terminate the malicious process. 

<img width="1002" height="596" alt="image" src="https://github.com/user-attachments/assets/1f2a585c-d617-4e96-ba76-cb4719d9ef04" />


## **4. Verification**
 The sensor confirmed the process termination, and the C2 channel on the attacker machine was immediately severed.

<img width="1002" height="626" alt="image" src="https://github.com/user-attachments/assets/5e6b6757-a802-4be2-bb27-e00bab305fe2" />


<img width="872" height="495" alt="image" src="https://github.com/user-attachments/assets/bde4d4ff-316b-4228-b12c-8e62aa9f7407" />


---

---

### 🔮 Roadmap & Future Development
This lab is a living project currently under active development.
* **Automated Defense:** Currently developing custom LimaCharlie D&R rules to automate the blocking of Port 8888 C2 traffic.
* **Payload Variation:** Expanding the attack simulation to test EDR resilience against obfuscated payloads.

### 📄 Full Report
For a detailed technical breakdown, including error logs and remediation steps, download the full report:
[📥 **Download Lab_Report_FINAL.pdf**](./Lab_Report_FINAL.pdf)
