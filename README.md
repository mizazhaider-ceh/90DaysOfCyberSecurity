<h1 align="center">90 Days of Cyber</h1>

<p align="center">
  <img src="https://img.shields.io/badge/90%20days-hands--on-blue" alt="90 days, hands-on" />
  <img src="https://img.shields.io/badge/cost-free-brightgreen" alt="Cost: free" />
  <img src="https://img.shields.io/badge/license-MIT-yellow" alt="License: MIT" />
  <img src="https://img.shields.io/badge/made%20by-The%20PenTrix-7C3AED" alt="Made by The PenTrix" />
</p>

<p align="center">
  A 90-day, hands-on cybersecurity study plan that takes you from zero to job-ready fundamentals. One to two hours a day, every tool free, every single day ends with something you built, broke, or captured yourself.
</p>

> This plan has opinions. Most roadmaps are link lists. This one is a workout program: networking before hacking, Linux before Python, web fundamentals before Burp, and a real vulnerable lab (not screenshots of one) when it is time to attack. Follow it in order and you will finish with skills you can demonstrate, not just videos you watched.

## Contents

- [How to use this plan](#how-to-use-this-plan)
- [The 90 days at a glance](#the-90-days-at-a-glance)
- [Phase breakdown](#phase-breakdown)
- [Hands-on labs](#hands-on-labs)
- [Track your progress](#track-your-progress)
- [Curated resources](#curated-resources)
- [FAQ](#faq)
- [Author](#author)
- [Contributing](#contributing)
- [License](#license)

## How to use this plan

**Budget 1 to 2 hours a day.** Every day is scoped for that. Some days will take less, a few will take more, and that is fine.

**Go in order.** Each phase assumes the one before it. You cannot enjoy web hacking in phase 5 if you skipped the Linux terminal in phase 3.

**Everything is free.** Every tool, platform tier, and resource in this plan has a free option. If something asks for a card, there is a free tier or a free alternative named in the day's task.

**Track your progress.** Each day ends with a checkbox. Check it only when the hands-on task is actually done. Fork this repo and check them off in your own copy, or print the [progress list](#track-your-progress) and pin it to your wall.

**Build in public.** From phase 6 onward you will push your scripts, notes, and writeups to GitHub. Employers hire people who can show their work.

## The 90 days at a glance

| Days | Phase | What you will be able to do |
|------|-------|------------------------------|
| 1-7 | [Networking Fundamentals](phases/phase-01-networking.md) | Read a network like a map, capture traffic with Wireshark, scan with nmap |
| 8-14 | [Security Foundations](phases/phase-02-security-foundations.md) | Think in CIA triad terms, hash and crack, spot phishing on sight |
| 15-28 | [Linux Command Line](phases/phase-03-linux.md) | Live in the terminal, script in bash, clear Bandit levels |
| 29-42 | [Python for Security](phases/phase-04-python.md) | Write your own tools, parse logs, build a port scanner |
| 43-56 | [Web Hacking with the PenTrix VulnLab](phases/phase-05-web-hacking.md) | Intercept traffic with Burp, exploit real vulnerabilities, earn 50 flags |
| 57-63 | [Git and GitHub](phases/phase-06-git.md) | Version everything, publish your work, collaborate with pull requests |
| 64-70 | [SIEM and Blue Team Basics](phases/phase-07-elk-siem.md) | Hunt threats in logs with the Elastic Stack, write an incident note |
| 71-77 | [Cloud Security Basics](phases/phase-08-cloud.md) | Secure AWS and Azure resources the way attackers see them |
| 78-84 | [Review and Guided Practice](phases/phase-09-review-practice.md) | Solve TryHackMe, HackTheBox, and picoCTF challenges against the clock |
| 85-90 | [Capstone: Prove Your Skills](phases/phase-10-capstone.md) | Finish kill-chain scenarios, ship a project, write a professional writeup |
| 91-95 | Career ([resume](career/resume.md), [job search](career/job-search.md)) | A one-page resume, a clean GitHub, and a real job search plan |

## Phase breakdown

**Phase 1: Networking Fundamentals** (days 1-7). Packets are the alphabet of everything in security, so the plan starts here. You map your own home network, learn the OSI and TCP/IP models by matching real activities to layers, memorize the ports that matter, and finish the week capturing your own traffic in Wireshark and scanning your network with nmap. [Open the phase file](phases/phase-01-networking.md)

**Phase 2: Security Foundations** (days 8-14). The mental models before the tools: the CIA triad, malware types, how hashing differs from encryption, why MFA matters, and how phishing actually works when you read the headers. You will hash a file yourself, check your own exposure, and dissect a real phishing email safely. [Open the phase file](phases/phase-02-security-foundations.md)

**Phase 3: Linux Command Line** (days 15-28). Two full weeks in the terminal, because every serious security role lives there. Filesystem, permissions, processes, SSH, pipes, grep, sed, awk, then bash scripting with a real script you write, and OverTheWire Bandit to prove it stuck. [Open the phase file](phases/phase-03-linux.md)

**Phase 4: Python for Security** (days 29-42). Python is the duct tape of security work. Two weeks from variables to sockets: you will write a port scanner, parse logs with regex, fetch web pages with requests, and finish with a log analyzer project pushed to GitHub. [Open the phase file](phases/phase-04-python.md)

**Phase 5: Web Hacking with the PenTrix VulnLab** (days 43-56). The heart of the plan. You learn HTTP properly, set up Burp Suite Community, then spend twelve days exploiting real vulnerabilities in a real lab: SQL injection, XSS, broken auth, IDOR, SSRF, file uploads, command injection, JWT flaws, XXE, SSTI, and race conditions. The milestone is 50 earned flags and a written writeup of your favorite exploit. [Open the phase file](phases/phase-05-web-hacking.md)

**Phase 6: Git and GitHub** (days 57-63). A breather week that pays off forever. Branching, merging, remotes, READMEs, the branching game, and a polished profile, ending with your first real pull request. [Open the phase file](phases/phase-06-git.md)

**Phase 7: SIEM and Blue Team Basics** (days 64-70). You switch sides. The Elastic Stack in Docker, KQL searches, Sigma detection rules, Windows event IDs that matter, the MITRE ATT&CK framework, and a final exercise where you attack your own machine and find yourself in the logs. [Open the phase file](phases/phase-07-elk-siem.md)

**Phase 8: Cloud Security Basics** (days 71-77). The shared responsibility model, a free AWS account with IAM done right, S3 misconfigurations on your own bucket, Azure via Microsoft Learn, Docker in the browser, and a strict cleanup day so the free tier stays free. [Open the phase file](phases/phase-08-cloud.md)

**Phase 9: Review and Guided Practice** (days 78-84). Consolidation week on the big training platforms: TryHackMe rooms, HackTheBox Starting Point machines, picoCTF challenges, a review of your weakest days, and timed redos of labs you have already solved. [Open the phase file](phases/phase-09-review-practice.md)

**Phase 10: Capstone: Prove Your Skills** (days 85-90). Six days that turn practice into proof. Full kill-chain scenarios in the VulnLab, the hardest modules you skipped, a professional writeup of a platform challenge, a published GitHub project, and a written retrospective with your next 90 days planned. [Open the phase file](phases/phase-10-capstone.md)

**Career: resume and job search** (days 91-95). Turning 90 days of work into a job: a one-page resume that reads like experience, a GitHub and LinkedIn cleanup, an application tracker, and interview prep with labs you can talk through. [Build your resume](career/resume.md) and [land the job](career/job-search.md)

## Hands-on labs

> Reading about vulnerabilities does not teach exploitation. These labs give you legal, safe targets to practice on, and they are woven into the daily tasks, not parked in an appendix.

| Lab | What it is | When you use it |
|-----|-----------|-----------------|
| **PenTrix VulnLab** (https://github.com/mizazhaider-ceh/PenTrix-VulnLab) | The plan's home lab for web hacking. An intentionally vulnerable web app with 201 challenges across 29 modules, each its own small website, running locally with docker compose. Flags are earned only by genuine exploitation. | Daily in phases 5 and 10 |
| **TryHackMe** (https://tryhackme.com) | Guided rooms with a free tier. | Phase 9, for networking, Linux, and Burp rooms |
| **HackTheBox** (https://www.hackthebox.com) | Realistic machines with a free tier. | Phase 9 for Starting Point machines, phase 10 for writeup practice |
| **picoCTF** (https://picoctf.org) | Free CTF challenges, great for timed practice. | Phase 9 |
| **OverTheWire Bandit** (https://overthewire.org/wargames/bandit/) | Linux wargame over SSH. | End of phase 3 |

## Track your progress

Copy this into your fork and check phases off as you finish them.

- [ ] Phase 1: Networking Fundamentals (days 1-7)
- [ ] Phase 2: Security Foundations (days 8-14)
- [ ] Phase 3: Linux Command Line (days 15-28)
- [ ] Phase 4: Python for Security (days 29-42)
- [ ] Phase 5: Web Hacking with the PenTrix VulnLab (days 43-56)
- [ ] Phase 6: Git and GitHub (days 57-63)
- [ ] Phase 7: SIEM and Blue Team Basics (days 64-70)
- [ ] Phase 8: Cloud Security Basics (days 71-77)
- [ ] Phase 9: Review and Guided Practice (days 78-84)
- [ ] Phase 10: Capstone (days 85-90)
- [ ] Career: resume and job search (days 91-95)

## Curated resources

The full resource list lives in [learn.md](learn.md): courses, docs, tools, practice platforms, and YouTube educators, grouped by topic, with links only to resources that definitely exist.

## FAQ

<details>
<summary><strong>Do I need any experience to start?</strong></summary>

No. Day 1 assumes you can use a computer and a browser. Everything else is taught in order.
</details>

<details>
<summary><strong>How much time does this take per day?</strong></summary>

One to two hours. A few lab days run longer if you get hooked, which is the point.
</details>

<details>
<summary><strong>Is everything really free?</strong></summary>

Yes. Every tool and platform in the plan has a free tier or is open source. The cloud phase warns you before anything could cost money and ends with a cleanup day.
</details>

<details>
<summary><strong>Can I skip to the hacking part?</strong></summary>

You can, but you will be slower at it. Phases 1 through 4 are what make phase 5 fun instead of frustrating.
</details>

<details>
<summary><strong>Windows or Mac?</strong></summary>

Either works for the early phases. In phase 3 you install a Linux VM, and from then on most hands-on work happens in Linux.
</details>

<details>
<summary><strong>What if I fall behind?</strong></summary>

The days are numbered, not dated. Miss a week, pick up where you left off. Phase 9 exists specifically to repair weak spots.
</details>

<details>
<summary><strong>Will this get me a job?</strong></summary>

It gives you demonstrable fundamentals: a GitHub with real projects, labs you can talk through, and the vocabulary to survive a junior interview. Days 91 to 95 turn that into applications. No plan replaces persistence, but this one replaces wondering what to learn next.
</details>

<details>
<summary><strong>Is hacking these labs legal?</strong></summary>

Everything here targets your own machines, your own cloud accounts, or platforms built for practice. Never test systems you do not own or have written permission to test.
</details>

## Author

**Muhammad Izaz Haider**, building as **The PenTrix**. Cybersecurity student, penetration tester, and builder of the PenTrix VulnLab.

> I made the plan I wished existed when I started: no fluff, a lab every day, and an order that actually makes sense.

- GitHub: https://github.com/mizazhaider-ceh
- LinkedIn: https://www.linkedin.com/in/muhammad-izaz-haider-091639314/
- Portfolio: https://www.mizazhaider-ceh.dev/

## Contributing

Found a broken link, a better free resource, or a typo? Open an issue or a pull request. Keep the rules: every day needs a hands-on task, everything stays free, and every URL must be real.

## License

MIT. See [LICENSE](LICENSE). Copyright (c) 2026 Muhammad Izaz Haider.
