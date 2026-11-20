<div align="center">


<img width="1007" height="831" alt="Copilot_20261027_105204" src="https://github.com/user-attachments/assets/b2c4ae05-abb6-4cbe-94e3-65bbfaa1a0fd" />

# 🛡️ PASSWORD CRACKING USING JOHN THE RIPPER 

### 🔎 PASSWORD HASHES & CRACKING 



<img src="https://img.shields.io/badge/CYBERSECURITY-NETWORKWALKS-0A66C2?style=for-the-badge&logo=hackthebox&logoColor=white" />
<img src="https://img.shields.io/badge/WEEK%303-B084-6F42C1?style=for-the-badge" />
<img src="https://img.shields.io/badge/PERMITTED-YES-22C55E?style=for-the-badge" />





**W3-PM-FINAL | CYBERSECURITY |  NETWORKWALKS**


## Purpose:

Documenting a major milestone in my cybersecurity training understanding how cryptographic password hashes work and using industry tools to audit and test password strength on encrypted files.



## 📑 TABLE OF CONTENTS


 • Overview
• Module 1: Password Cracking with John the Ripper (JTR)
 • Prerequisites & Setup
 • Step-by-Step Walkthrough
 • Verification & Result
• Module 2: Browser-Based Cracking with Networkwalks (NW)
 • Tools Used
 • Step-by-Step Walkthrough
• Tool Comparison
• Key Takeaways & Defense
• Disclaimer









### 🔍 OVERVIEW


Passwords are rarely stored or verified in plaintext; instead, systems use cryptographic hashes to represent them. In this lab, I explored how hashes are extracted from password-protected files (specifically encrypted PDFs) and how offline/online cracking tools recover the original plaintext passwords.




## 🛠️ Module 1: Password Cracking with John the Ripper (JTR)


John the Ripper (JTR) is an open-source password security auditing and recovery tool. It supports hundreds of hash and cipher types, including encrypted archives (ZIP, RAR), Office documents, and PDFs.



[!NOTE]
Johnny is the official GUI (Graphical User Interface) frontend for John the Ripper. It provides a point-and-click workflow, allowing beginners to run password attacks without memorizing complex CLI flags.




## Prerequisites & Setup



1. Download JTR: Visit the official Openwall website and download the binary matching your OS (Windows, Linux, or macOS). Extract the archive to a dedicated folder.
2. Install Johnny (GUI): Download and run the Johnny installer from the official repository.
3. Link JTR to Johnny: Open Johnny, navigate to Settings, click Browse, and point it directly to your john.exe executable.




## Step-by-Step Walkthrough


Step Action Details
1 Acquire Target Download the target password-protected PDF file to your local machine.
2 Extract Hash Upload the encrypted PDF to a hash-extraction utility (or use pdf2john) to isolate the file's hash string.
3 Sanitize Hash Copy the extracted hash and paste it into a clean .txt file (e.g., hash.txt).
4 Load in Johnny Open Johnny, click Open Password File, select your hash.txt, and click Open.
5 Execute Attack Click Start New Attack to begin testing wordlists and rule mutations against the hash.



[!WARNING]
Hash Formatting Pitfall: Before saving your hash.txt file, inspect the start of the string. If you see extra characters like a leading b' or b (common Python byte-string markers from web extractors), remove them. Leaving them in will cause JTR to fail to recognize the hash format.





### Verification & Result

Once JTR finds a match, Johnny displays the recovered plaintext password in the interface. Entering this password into the locked PDF successfully decrypts and opens the document, confirming a successful audit.



### 🌐 Module 2: Browser-Based Cracking with Networkwalks (NW)

To understand how cloud/web-based utilities streamline this workflow without local installations, I replicated the exercise using Networkwalks' free browser tools.


## Tools Used

• NW Hash Calculator: Parses encrypted files to extract raw hash signatures.
• NW Password Cracker: Runs dictionary/brute-force attacks against submitted hashes in the browser.



Step-by-Step Walkthrough

1. Prepare Target: Ensure the encrypted PDF is saved locally on your computer.
2. Extract Hash: Open the Networkwalks Hash Calculator in your browser and upload the locked PDF.
3. Copy Signature: Wait for the tool to return the hash string (for PDFs, this typically starts with $pdf$...) and copy the entire value.
4. Launch Attack: Open the Networkwalks Password Cracker, paste the $pdf$ hash into the input field, and start the attack.
5. Unlock File: Once the tool resolves the plaintext password, copy it and unlock the local PDF to verify access.




### ⚖️ Tool Comparison


 1 Feature John the Ripper + Johnny (Local) Networkwalks Tools (Web)
Installation Required (Local binaries + GUI) None (100% Browser-based)
Privacy / OpSec High (Files never leave your machine) Low (Files/hashes are uploaded to a third party)
Customization High (Custom wordlists, rules, modes) Limited (Pre-configured server wordlists)
Best Use Case Real-world audits & sensitive files Quick labs & non-sensitive test files





### 💡 Key Takeaways & Defense

• How Cracking Works: Attackers rarely reverse a hash mathematically. Instead, tools rapidly hash millions of candidate passwords (from wordlists like rockyou.txt) until the output matches the target file's hash.
• OpSec Matters: While browser-based crackers are great for learning, sensitive or proprietary files should only be audited locally using offline tools like JTR.
• Defensive Posture: Simple or dictionary-based passwords can be cracked in seconds. Enforcing long passphrases (14+ characters) with high entropy drastically increases the time and compute power required to crack a hash.




### ⚠️ Disclaimer

This repository and write-up are shared strictly for educational and authorized security research purposes only. The tools and techniques documented here should only ever be used on files, networks, and systems that you own or have explicit, written permission to test.


### Evidence Collected 

<img width="1280" height="1157" alt="image" src="https://github.com/user-attachments/assets/9ac0a3ab-43d0-4e4e-aa27-69b05abe806b" />
<img width="905" height="1280" alt="image" src="https://github.com/user-attachments/assets/57fb24e5-b61a-4925-a9c9-33affb23cb86" />


