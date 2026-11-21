# Password Cracking with NetworkWalks Tools

Week 3, Project Module 2, Cybersecurity & Ethical Hacking lab.

## Goal
Recover the password of a locked PDF by extracting its hash and cracking it with free browser-based tools. No installs needed.

## Background
A password-protected PDF stores its password as a hash, a one-way scrambled value. To recover the password, extract that hash from the file and run it through a cracker that tries candidate passwords until one matches. Short or common passwords fall quickly.

## Tools
- **NetworkWalks Hash Calculator** (https://networkwalks.com/hash-calculator/): extracts the `$pdf$...` hash from the locked file. Parsing runs locally in the browser, so the file is not uploaded.
- **NetworkWalks Password Cracker** (https://networkwalks.com/password-cracker/): runs the attack against the hash.

## Steps

### 1. Download the locked PDF
Downloaded the encrypted PDF from the lab page.

![Locked PDF uploaded to the Hash Calculator](screenshots/02-hash-calculator-pdf-uploaded.png)

### 2. Extract the hash
Uploaded the PDF to the Hash Calculator. The tool detected encryption and extracted a crackable hash. Details shown: Revision R4, Version V4, 128-bit key.

![Extracted PDF hash](screenshots/03-hash-calculator-hash.png)

### 3. Copy the full hash
Copied the complete hash, starting from `$pdf$`. The hash wraps across three lines in the UI, so the copy must include all of them.

### 4. Crack the hash
Pasted the hash into the Password Cracker and started the attack.

<!-- SCREENSHOT: Password Cracker with hash pasted -->
<!-- SCREENSHOT: Cracking result -->

### 5. Open the PDF
Entered the recovered password in the locked PDF. It opened, which completed the lab.

<!-- SCREENSHOT: PDF opened with password -->

## Lessons Learned
- **Hash extraction is fast and client-side.** The whole step took under a minute, and the hash was ready to copy right after upload.
- **The hash header reveals the encryption.** `$pdf$4*4*128` means R4 revision, V4 version, 128-bit key. Knowing the scheme helps estimate how hard the crack will be.
- **Copy the whole hash.** It wraps across lines, and a partial copy will fail or give a wrong result. Check that the paste starts at `$pdf$` and ends at the last character.
- **Check the file name against the instructions.** The lab text refers to "My Locked PDF1.pdf", but the file I used was "My Locked PDF3.pdf". Confirm you have the file the lab asks for before you start.
- **Crack time depends on password strength.** Short, common passwords are found quickly. Longer, mixed-character passwords can take years. This is the core reason to use long passwords.
- **Password-protected files are only as safe as their password.** Anyone with the file can run this same attack offline.

## Takeaways
- Use a password manager and a unique, long passphrase for every protected file.
- Treat hashes as sensitive. Anyone who gets the hash can attempt offline cracking.
- Understand the tool's output before you trust it. Read the encryption details, not just the final password.

## Environment
Windows laptop, Chrome browser.

## Disclaimer
Performed on a lab file provided by NetworkWalks for educational purposes only.
