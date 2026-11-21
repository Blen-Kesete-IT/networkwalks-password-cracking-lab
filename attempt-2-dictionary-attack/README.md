# Attempt 2: Dictionary Attack on a Second Locked PDF

Follow-up to the first cracking lab (see ../README.md). Same method, different file, and this time I ran the attack in the Dictionary Attack Lab, which shows the cracking progress live.

## Goal
Extract the hash from a second locked PDF and recover its password with a dictionary attack, the same idea John the Ripper uses.

## Steps

### 1. Extract the hash
Uploaded "My Locked PDF2.pdf" (204.7 KB) to the Hash Calculator. It reported an encrypted file and extracted a crackable hash.

- Revision R4, Version V4, 128-bit key (the same settings as the first file)
- Hash starts with `$pdf$4*4*128*-1028*1*16*...`

<!-- SCREENSHOT: screenshots/01-hash-calculator-pdf2-hash.png (upload via GitHub web UI) -->

### 2. Run the dictionary attack
Pasted the hash into the Password Cracker through Dictionary Attacks. The tool hashes each word in a wordlist and compares it to the PDF hash.

- Wordlist size: 100 words
- Speed: about 9 passwords per second
- The attack reached 91 of 100 words before it found a match. The match came near the end of the list.

### 3. Open the PDF
Entered the recovered password in the locked PDF. It opened, which completed the lab.

## Lessons Learned
- **A dictionary attack only works if the password is in the list.** A 100-word list is tiny. Real attacks use wordlists with millions of entries, such as rockyou.txt, because they cover common passwords people actually use.
- **Common passwords fall fast.** The password was a simple word with a digit added, which is one of the first patterns attackers try. Adding digits to a common word is not real protection.
- **Speed depends on the hash and the tool.** At about 9 guesses per second in the browser, the attack took only a few seconds for 100 words. Offline cracking tools run far faster, so a longer list gets tested much more quickly.
- **Same encryption, different result.** Both PDFs use R4 V4 with a 128-bit key, so the encryption is the same. The difference in crack time came from the password itself, not the encryption.
- **Verify the file you're working on.** Each lab uses a different PDF (PDF1, PDF2, PDF3). Check the file name in the Hash Calculator before you start the cracker.

## Takeaways
- Choose long passphrases over short words with digits. Random long passphrases are not in common wordlists.
- Watch for a pattern in your own passwords. If a password fits common patterns, assume an attacker will try it.
- Treat password-protected files as only as secure as their password.

## Notes
The flag and the recovered password are not shown in this write-up, following the same approach as the first lab.

## Environment
Windows laptop, Chrome browser.

## Disclaimer
Performed on a lab file provided by NetworkWalks for educational purposes only.
