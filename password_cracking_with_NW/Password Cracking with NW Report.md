# Penetration Testing Report

### Password Cracking with Network Walks (NW) Dictionary Attack Lab

**W3-PM2 | Cybersecurity | Password Cracking Lab**

| Field | Details |
| --- | --- |
| **Pentester Name** | Aagnick Naha |
| **Program / Batch** | Network Walks Cybersecurity Lab |
| **Date** | 17 November 2026 |
| **Modules Completed** | Password Cracking with NW Tools / Dictionary Attack Lab |
| **Client / Target** | 1. My Locked PDF1.pdf in the authorized training environment |
| **Permission Secured?** | Yes |
| **Phases Covered** | **Phase 1:** Hash extraction and validation <br> **Phase 2:** Dictionary attack using a wordlist <br> **Phase 3-5:** Verification, reporting, and evidence collection |

---

## 1. Liability Disclaimer

All work documented in this report was performed in an authorized training environment or on systems owned and controlled by the operator for academic purposes. This activity was designed to illustrate password recovery techniques in a controlled setting and must not be applied to unauthorized targets or real-world systems without proper approval.

---

## 2. Introduction

This report documents the second password-cracking exercise, performed using a Network Walks dictionary attack lab. The focus was on deriving a PDF hash, comparing it against a wordlist, and validating the recovered password when the correct candidate was found. This lab highlighted both the mechanics of PDF hash cracking and the weakness of predictable passwords in common user workflows.

The exercise followed a consistent process: extract the hash, prepare the attack input, test a list of candidate passwords, and confirm the result by opening the protected PDF. The environment used both a custom lab interface and a John the Ripper–style attack workflow aligned with typical dictionary attack principles.

---

## 3. Tools Used

| Tool | Purpose |
| --- | --- |
| Hash Calculator | Extracts and displays the PDF hash to be attacked |
| Dictionary Attack Lab | Tests a list of candidate passwords against the PDF hash |
| John the Ripper / JTR logic | Validates the general cracking methodology and wordlist attack process |
| PDF viewer / password prompt | Confirms the recovered password by opening the protected file |

---

## 4. Activities Performed

### 4.1 Hash Extraction and Preparation

**Objective:** Extract the password hash from the PDF file and prepare it for dictionary testing.

**Target:** My Locked PDF1.pdf

**Step 1: Extract PDF hash**

- Command: Use the Hash Calculator / uploaded PDF to generate a crackable PDF hash
- Observation: The hash was extracted successfully and displayed in the `$pdf$4*4*128*...` format.
- Evidence: Screenshot 2026-11-17 020009.png and Screenshot 2026-11-17 020020.png

![Hash extraction in NW tool](./Screenshot%202026-11-17%20020009.png)
![Hash validation result](./Screenshot%202026-11-17%20020020.png)

- Why it matters: This step converts the locked file into a format that can be rapidly tested against common passwords.

**Step 2: Confirm hash validity**

- Command: Review the extracted hash and validate the PDF encryption metadata
- Observation: The hash length, version, and key information were consistent with a PDF-based encryption scheme.
- Evidence: Screenshot 2026-11-17 020416.png

![Confirmation of PDF hash parameters](./Screenshot%202026-11-17%20020416.png)

- Why it matters: Correct format validation prevents wasted effort and identifies the proper attack vector.

### 4.2 Dictionary Attack Execution

**Objective:** Test the extracted PDF hash against a wordlist to recover the original password.

**Target:** My Locked PDF1.pdf

**Step 1: Load wordlist**

- Command: Start a dictionary attack using the built-in wordlist (`JTR_default_password.txt`)
- Observation: Candidate words were checked sequentially against the PDF hash.
- Evidence: Screenshot 2026-11-17 020757.png

![Dictionary attack running](./Screenshot%202026-11-17%20020757.png)

- Why it matters: Dictionary attacks are efficient when users select predictable, common, or weak passwords.

**Step 2: Match found**

- Command: Continue the attack until the match is found
- Observation: The password `good-luck` matched the hash and was reported as the valid PDF password.
- Evidence: Screenshot 2026-11-17 020835.png

![Password cracked successfully](./Screenshot%202026-11-17%20020835.png)

- Why it matters: This demonstrates how a weak password can be recovered quickly in a lab setting and reinforces the need for stronger password controls.

**Step 3: Validation**

- Command: Open the PDF using the recovered password
- Observation: The document opened successfully after the password was entered.
- Evidence: Final certificate screenshot in the project results set

![PDF access after password recovery](./Screenshot%202026-11-17%20020835.png)

- Why it matters: Confirmation of the match ensures the attack is valid and the result is trustworthy.

---

## 5. Risk Analysis and Impact

| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
| --- | --- | --- | --- | --- |
| 1 | Weak password recovery was successful via dictionary attack | The password `good-luck` was found using a common wordlist | Immediate document compromise if used on a real protected file | High |
| 2 | PDF protection was not resilient to low-entropy credentials | The hash was extracted and attacked offline without needing live system interaction | Loss of confidentiality for protected content | High |
| 3 | Predictable user-generated passwords increase exposure | The dictionary attack exposed the weakness in the chosen credential | Unauthorized document access, data loss, and possible compliance issues | Medium |

**Risk level key:** Critical, Medium, Low

These findings reflect educational testing outcomes in a controlled environment rather than a claim about unrelated real-world systems.

---

## 6. Recommendations

1. **Use strong, non-dictionary passwords** - Avoid common words, names, and low-complexity phrases.
2. **Enforce minimum password length and entropy** - Require longer and more random credentials to slow offline attacks.
3. **Use password managers** - Reduce the risk of users reusing or selecting weak passwords.
4. **Protect sensitive files with modern encryption** - Use strong PDF security settings and modern access controls.
5. **Limit and verify testing scope** - Only crack files or credentials that are authorized for ethical testing.

---

## 7. Conclusion

This Network Walks exercise demonstrated the effectiveness of a dictionary attack against a password-protected PDF. The attack began with a PDF hash extraction, moved into systematic wordlist testing, and concluded with the successful recovery of the password `good-luck`. The result reinforced an essential cybersecurity principle: if a password is weak, predictable, or based on common vocabulary, it is vulnerable to rapid offline attack.

The exercise also highlighted the value of strong password policy, modern encryption, and responsible testing. In a real environment, such weaknesses could lead to unauthorized access, data disclosure, and a broader compromise of confidentiality. The lab setting was useful for demonstrating the mechanics of the attack and the importance of defensive controls.

---

## 8. Evidence Collected

Screenshots collected during the practical activities are stored in the `password_cracking_with_NW` folder.

- Screenshot 2026-11-17 012913.png - Project file list and task context
- Screenshot 2026-11-17 012926.png - Password prompt / PDF access workflow in the training environment
- Screenshot 2026-11-17 020009.png - PDF hash extracted from the protected file
- Screenshot 2026-11-17 020020.png - Hash calculator showing validation details
- Screenshot 2026-11-17 020416.png - Wordlist attack environment and preparation screen
- Screenshot 2026-11-17 020757.png - Attack in progress against the PDF hash
- Screenshot 2026-11-17 020835.png - Successful password recovery (`good-luck`) and completion result

---

*End of report*
