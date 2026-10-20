# Phase 2: Security Foundations

Welcome to week two. This phase builds the core ideas that every security topic rests on. You will learn how security teams think about risk, what malware actually does, how cryptography protects data, and how attackers trick people instead of machines. Each day takes about one to two hours and ends with a real task you do yourself, so the ideas stick.

## Day 8: The CIA triad: confidentiality, integrity, availability
- **Learn:** The CIA triad is the three goals of security: confidentiality (only the right people see data), integrity (data is not changed or tampered with), and availability (systems and data work when you need them). A threat is anything that can cause harm, a vulnerability is a weakness an attacker can use, and risk is what you get when a threat meets a vulnerability.
- **Do:** Pick three things you use daily (for example your email, a banking app, and a cloud photo backup) and write one sentence for each describing which part of the CIA triad matters most for it and why.
- [ ] Done: three written examples, each naming one CIA property and a short reason

## Day 9: Malware types and how infections spread
- **Learn:** Malware comes in types: viruses need a host file and user action, worms spread on their own across networks, trojans pretend to be useful software, ransomware encrypts your files and demands payment, and spyware secretly watches what you do. Infections spread through email attachments, fake downloads, infected USB drives, malicious ads, and software cracks.
- **Do:** Visit the MITRE ATT&CK website (https://attack.mitre.org) and look up one technique used by malware, for example search for "phishing" or "scheduled task", then write two sentences explaining what the attacker achieves with it.
- [ ] Done: one ATT&CK technique found and explained in two sentences of your own words

## Day 10: Cryptography basics: hashing vs encryption, symmetric vs asymmetric
- **Learn:** Encryption scrambles data so it can be decrypted later with a key, while hashing turns data into a fixed fingerprint that cannot be reversed. Symmetric encryption uses one shared key for both sides, asymmetric encryption uses a public key to lock and a private key to unlock, which is how secure websites exchange keys safely.
- **Do:** Open CyberChef (https://gchq.github.io/CyberChef/) and paste the same short sentence twice, then apply the "To SHA256" recipe to both copies and confirm the two hashes match, then change one letter and see how the hash changes completely.
- [ ] Done: two identical hashes from identical input, plus one totally different hash after a one-letter change

## Day 11: Hashing in practice: hash a file and identify a mystery hash
- **Learn:** Files are checked with hashes to prove they downloaded correctly and were not tampered with, which is why software sites publish a SHA256 next to each download. Identifying an unknown hash is harder, because hashes are one-way, but common hashes from password lists can be matched against known databases.
- **Do:** Download any small free file (for example a text file or an image), run `sha256sum` on it in your terminal, write down the hash, then change nothing, run it again, and confirm the hash is identical.
- [ ] Done: one file hashed twice with matching output, hash recorded in your notes

## Day 12: Authentication: passwords, MFA, and password managers
- **Learn:** Authentication proves who you are, usually with a password (something you know), plus a second factor like a phone code (something you have), which together are called MFA. Reusing one password across sites is dangerous: when one site leaks it, attackers try the same password everywhere, so a password manager that creates unique passwords for each site fixes this.
- **Do:** Check your most-used email address on Have I Been Pwned (https://haveibeenpwned.com) to see if it appeared in any known data breach, then enable MFA on one important account (email, school, or banking) if you have not already.
- [ ] Done: breach check completed and noted, MFA enabled on at least one important account

## Day 13: Social engineering and phishing red flags
- **Learn:** Social engineering tricks people instead of hacking machines, and phishing is the most common form: fake emails or messages that push you to click a link, open an attachment, or reply with sensitive details. Red flags include urgency ("your account closes today"), mismatched sender addresses, links whose real destination differs from the shown text, unexpected attachments, and requests for passwords or payment.
- **Do:** Find a real phishing example safely (check the spam folder of an email account, or search a phishing example gallery) and list five red flags you spot, noting the sender address, the urgency trick, and what the link actually points to when you hover it without clicking.
- [ ] Done: five red flags written down for a real phishing example, including sender, urgency trick, and link destination

## Day 14: Security career map and week one to two review
- **Learn:** The field splits into teams: the blue team defends (SOC analysts watch alerts, incident responders handle breaches), the red team attacks legally (penetration testers find weaknesses), and GRC handles governance, risk, and compliance (policies, audits, standards). Roles like security engineer and malware analyst sit across these areas.
- **Do:** Reread your notes from Days 1 to 14, then write a one-page summary in your own words covering the three most important ideas from each week and pick one career path (blue, red, or GRC) that interests you most, with two sentences on why.
- [ ] Done: one-page review summary written, covering both weeks and naming one chosen career path with reasons
