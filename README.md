# BugHunt101

## Table of Contents
1. Project Overview  
2. Objectives  
3. Environment Setup  
4. Reconnaissance  
5. Vulnerability Assessment  
6. Proof of Concept  
7. Impact & Mitigation  
8. Screenshots  
9. Report   
10. Author Information  
11. Notes

---

## 1. Project Overview
This repository documents a beginner-friendly bug bounty exercise conducted on the **Damn Vulnerable Web Application (DVWA)**.  
The project demonstrates the full bug bounty workflow from reconnaissance to professional reporting in a **controlled lab environment**.

---

## 2. Objectives
- Learn and practice the bug bounty workflow in a safe environment  
- Perform reconnaissance using network scanning and directory discovery tools  
- Identify and safely exploit a reflected XSS vulnerability  
- Document findings with screenshots and a professional report  

---

## 3. Environment Setup
- DVWA installed locally on Kali Linux  
- Apache and MariaDB configured successfully  
- DVWA database reset for a clean testing environment  

**DVWA Credentials:**  
- Username: `admin`  
- Password: `password`

---

## 4. Reconnaissance
- Target URL recorded in `recon/target.txt`  
- Nmap scan executed:
nmap -sV -p- localhost

yaml
Copy code

**Open Services Identified:**  
- Port 80/tcp → Apache HTTP Server  
- Port 3306/tcp → MariaDB  

---

## 5. Vulnerability Assessment
- DVWA security level set to **Low**  
- Navigated to **XSS (Reflected)** module  
- Tested payload:
## Vulnerability Testing – XSS (Reflected)

The following payload was tested on DVWA with the security level set to Low.

Payload used:
<script>alert(1)</script>

Result:
XSS alert popup appeared, confirming the vulnerability.

Impact Validation Payload:
<script>alert(document.cookie)</script>

Result:
Cookie disclosure confirmed successful exploitation.

---

## 6. Proof of Concept (PoC)

Steps to reproduce:
1. Login to DVWA using valid credentials
2. Set security level to Low
3. Navigate to XSS (Reflected) page
4. Paste payload <script>alert(1)</script> and submit
5. Observe alert popup
6. Optional: Use <script>alert(document.cookie)</script> for cookie access

---

## 7. Impact & Mitigation

Impact:
- Execution of arbitrary JavaScript in a user’s browser
- Cookie theft and possible session hijacking
- Phishing and unauthorized actions in real-world applications

Mitigation:
- Sanitize and validate all user input
- Encode output before rendering
- Use secure frameworks or libraries
- Perform regular vulnerability testing

---

## 8. Screenshots

Security level set to Low:

<img width="751" height="552" alt="image" src="https://github.com/user-attachments/assets/d78e1115-0103-464c-9967-382978767809" />

XSS alert popup:

<img width="501" height="127" alt="image" src="https://github.com/user-attachments/assets/bac5c858-05c2-480b-b8c4-61b3415e6383" />

Cookie disclosure:

<img width="538" height="202" alt="image" src="https://github.com/user-attachments/assets/2cd9f3ae-474b-41b0-8b7a-83ae806029f9" />

All screenshots are available in the screenshots/ folder.

---

## 9. Report

The full vulnerability report is provided in PDF format:
bugbounty repo.pdf

---

## 10. Author Information

Name: Tooba Zainab  
Date: 16 January 2026  
Course: Cyber Security Lab  
Project: Bug Hunt 101 — Recon to Report  
Target Application: DVWA (Damn Vulnerable Web Application)

---

## 11. Notes

All testing was conducted in a controlled, local lab environment.  
This project demonstrates the full workflow from reconnaissance to professional reporting.  
Strictly for educational purposes.
