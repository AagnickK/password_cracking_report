# Penetration Testing Report

### Password Cracking with John the Ripper (JTR)

**W3-PM1 | Cybersecurity | Password Cracking Lab**

| Field | Details |
| --- | --- |
| **Pentester Name** | Aagnick Naha |
| **Program / Batch** | Network Walks Cybersecurity Lab |
| **Date** | 17 November 2026 |
| **Modules Completed** | Password Cracking with John the Ripper |
| **Client / Target** | 1. My Locked PDF1.pdf in the authorized training environment |
| **Permission Secured?** | Yes |
| **Phases Covered** | **Phase 1:** Hash extraction and format identification <br> **Phase 2:** John the Ripper password recovery <br> **Phase 3-5:** Validation, reporting, and evidence collection |

---

## 1. Liability Disclaimer

All activities in this report were performed only in a self-owned or course-authorized lab environment. The purpose was to practice ethical cybersecurity fundamentals, including hash extraction and password auditing on files that were intentionally protected for educational use. No unauthorized testing or illegal activity was conducted.

---

## 2. Introduction

This report documents the password-cracking exercise completed against a password-protected PDF using John the Ripper. The activity focused on extracting the PDF hash, identifying the encryption format, applying a cracking method, and verifying the recovered password. The workflow followed a structured process of extraction, validation, and evidence collection.

The environment was a local lab setup using Windows-based tools and password-protected PDF samples. Each stage included hash extraction, tool observations, evidence capture, and analysis of why the result matters in real-world security settings.

---

## 3. Tools Used

| Tool | Purpose |
| --- | --- |
| pdf2john | Extracts the PDF hash from an encrypted file so it can be cracked |
| John the Ripper (JTR) | Tests candidate passwords against the extracted PDF hash |
| Hashcat | Cross-checks password cracking workflow and hash format |
| PDF viewer / password prompt | Validates the recovered password against the encrypted file |

---

## 4. Activities Performed

### 4.1 PDF Hash Extraction

**Objective:** Extract the encrypted PDF hash and confirm the password protection mechanism.

**Target:** My Locked PDF1.pdf

**Step 1: pdf2john**

- Command: `pdf2john "My Locked PDF1.pdf" > pdf_hash_1.txt`
- Observation: The tool returned a PDF hash beginning with `$pdf$4*4*128*...`, confirming the file was protected using a crackable PDF format.
- Evidence: Screenshot 2026-11-17 013006.png

![Hash extraction result](./Screenshot%202026-11-17%20013006.png)

- Why it matters: This provides the exact material needed to test candidate passwords and confirms the protection method.

**Step 2: Hash inspection**

- Command: `cat pdf_hash_1.txt`
- Observation: The extracted hash included the revision, version, key length, and encrypted value necessary for cracking.
- Evidence: Screenshot 2026-11-17 013305.png

![PDF hash inspection](./Screenshot%202026-11-17%20013305.png)

- Why it matters: Hash review confirms the file is a standard PDF password object and identifies the appropriate attack strategy.

### 4.2 John the Ripper Recovery

**Objective:** Recover the password from the PDF hash using a structured cracking workflow.

**Target:** My Locked PDF1.pdf

**Step 1: Open password file in JTR**

- Command: Open the hash file in John the Ripper / Johnny
- Observation: John recognized the hash and presented the file in a crackable format.
- Evidence: Screenshot 2026-11-17 013344.png and Screenshot 2026-11-17 013408.png

![Open hash in Johnny](./Screenshot%202026-11-17%20013344.png)
![Johnny loaded hash](./Screenshot%202026-11-17%20013408.png)

- Why it matters: Correct detection of the hash type ensures the attack is valid and efficient.

**Step 2: Start the attack**

- Command: John / Johnny dictionary attack against the PDF hash
- Observation: The candidate password eventually matched the protected PDF.
- Evidence: Screenshot 2026-11-17 013512.png and Screenshot 2026-11-17 013533.png

![Cracking in progress](./Screenshot%202026-11-17%20013512.png)
![Password match found](./Screenshot%202026-11-17%20013533.png)

- Why it matters: Successful cracking proves the password was weak enough for a dictionary-based or low-complexity attack in the lab environment.

**Step 3: Validate the password**

- Command: Open the PDF file using the recovered password
- Observation: The PDF opened successfully with the password `good-luck`.
- Evidence: Screenshot 2026-11-17 013546.png

![Recovered password validation](./Screenshot%202026-11-17%20013546.png)

- Why it matters: Validation confirms the recovered credential is correct and prevents false positives.

---

## 5. Risk Analysis and Impact

| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
| --- | --- | --- | --- | --- |
| 1 | Weak PDF password enabled offline recovery | The recovered password was `good-luck`, which was quickly discovered with a dictionary-based attack | Sensitive document contents could be exposed if the same weakness existed in a real system | Medium |
| 2 | Encrypted PDF hash was exposed and crackable | The hash was extracted and analyzed from the file in clear text format | Attackers could use the hash to test candidate passwords offline | Medium |
| 3 | Password reuse and weak complexity increase attack success | The password was low entropy and easily enumerated | Unauthorized file access, leakage of confidential information, and document compromise | High |

**Risk level key:** Critical, Medium, Low

These findings were identified in a controlled laboratory exercise and reflect the importance of strong password policy, not a claim about any unrelated production environment.

---

## 6. Recommendations

1. **Use strong, unique PDF passwords** - Passwords should be long, random, and different from common dictionary terms.
2. **Prefer modern encryption standards** - Prefer AES-based protection and current PDF security settings over legacy weak implementations.
3. **Use password managers** - Centralized password management reduces human-chosen weak password patterns.
4. **Apply defense-in-depth** - Pair access controls with encryption, secure storage, and audit logging.
5. **Conduct testing only within scope and authorization** - Ethical testing must be performed only on systems with explicit permission.

---

## 7. Conclusion

This exercise demonstrated how a password-protected PDF can be evaluated using standard forensic and cracking techniques. The process began with PDF hash extraction, moved into format validation, and culminated in a successful John the Ripper recovery of the password `good-luck`. The activity highlighted how weak passwords remain vulnerable to offline guessing and dictionary attacks when proper controls are not enforced.

The key learning outcome was that even a protected document is only as secure as the credential used to lock it. Hash extraction and password testing are legitimate defensive and educational activities when completed within scope and on authorized systems, reinforcing the value of strong passwords, modern encryption, and ethical testing culture.

---

## 8. Evidence Collected

Screenshots collected during the practical activities are stored in the `password_cracking_with_JTR` folder.

- Screenshot 2026-11-17 012913.png - PDF list and project file structure in the lab environment
- Screenshot 2026-11-17 013006.png - Extracted PDF hash from the protected file
- Screenshot 2026-11-17 013305.png - Hash validation and file format identification
- Screenshot 2026-11-17 013344.png - Johnny / JTR opening password file
- Screenshot 2026-11-17 013512.png - Password cracking process in progress
- Screenshot 2026-11-17 013546.png - Final password recovery and lab success certificate with captured flag

---

*End of report*
