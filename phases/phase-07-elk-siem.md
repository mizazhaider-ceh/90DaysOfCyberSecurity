# Phase 7: SIEM and Blue Team Basics

A SIEM (Security Information and Event Management) collects logs from many systems in one place so a security analyst can search them, spot attacks, and respond. In this phase you build your own SIEM lab with the Elastic Stack, learn to search logs with KQL, load a Sigma detection rule, read Windows security events, and finish with a small blue-team exercise on your own machine.

## Day 64: What a SIEM is and where logs come from
- **Learn:** A SIEM gathers log messages from many sources, normalizes them into one format, and lets you search everything at once. Common sources are firewall logs (who connected to what), Windows security events (logons, process creation), and web server access logs (who visited which page).
- **Do:** On your computer, open a firewall log, a web server log, or any system log you can find (for example, /var/log/syslog on Linux) and read 10 lines. Write down in your own words what information each line carries: timestamp, source IP, and the action that happened.
- [ ] Done: I can name three log sources and explain what each one records

## Day 65: Install the Elastic Stack with Docker and ship your first logs
- **Learn:** Elasticsearch stores and searches logs, Kibana gives you a web dashboard to explore them, and Filebeat reads log files on a machine and ships them into Elasticsearch. The Elastic Stack has a free tier that is enough for a home lab.
- **Do:** Install Docker on your machine, then pull and run the Elasticsearch and Kibana images with Docker Compose (follow the official install guide at https://www.elastic.co). Open Kibana in your browser at http://localhost:5601 and use the "Add data" flow to send your first log messages into Elasticsearch.
- [ ] Done: I can open Kibana at localhost:5601 and see my own log data indexed in Elasticsearch

## Day 66: Searching logs in Kibana with KQL
- **Learn:** Kibana Query Language (KQL) is a simple filter syntax for finding what you need in a pile of logs. You can match exact values with a field and a colon (for example, `event.code : 4625`), combine conditions with AND, OR, and NOT, and use wildcards like `*` to match part of a value.
- **Do:** In Kibana Discover, search the logs you shipped yesterday and practice five queries: find one event by an exact value, combine two conditions with AND, exclude something with NOT, use a wildcard search on a hostname or file name, and save your best query as a saved search.
- [ ] Done: I can write KQL queries with exact matches, AND, NOT, and wildcards, and save a search in Kibana

## Day 67: Detection rules and the Sigma format
- **Learn:** A detection rule tells the SIEM what pattern of log events counts as suspicious, so it can alert an analyst automatically. Sigma is an open standard for writing detection rules in YAML that can be converted into queries for many SIEMs, including Elastic.
- **Do:** Visit https://github.com/SigmaHQ/sigma and download one sample Sigma rule for detecting a suspicious process (for example, a rule about encoded PowerShell). Read the YAML line by line, note the logsource, detection, and condition sections, and try translating the rule into a KQL query you could run in Kibana.
- [ ] Done: I can read a Sigma rule file and explain its detection logic in plain English

## Day 68: Windows event logs and Sysmon basics
- **Learn:** Windows records security events in the Event Viewer, and three event IDs show up constantly in blue-team work: 4624 (a successful logon), 4625 (a failed logon), and 4688 (a new process was created). Sysmon is a free Microsoft tool that adds richer detail, like full command lines and network connections, to the process creation events.
- **Do:** Open Event Viewer on a Windows machine (or on your Windows VM if you have one), filter the Security log for event IDs 4624, 4625, and 4688, and inspect three events. Write down what each one tells you: the account name, the source IP for the logon, or the process name and command line for 4688.
- [ ] Done: I can explain what event IDs 4624, 4625, and 4688 mean and read one of each in the Event Viewer

## Day 69: Incident response and the MITRE ATT&CK framework
- **Learn:** Incident response is the process a blue team follows when something bad is found: prepare (plan and tools ready), detect (spot the alert), contain (stop it from spreading), eradicate (remove the cause), and recover (restore normal service). The MITRE ATT&CK framework maps real attacker behavior into tactics (what the attacker wants, like persistence or exfiltration) and techniques (how they do it), so you can name what you are seeing.
- **Do:** Open https://attack.mitre.org in your browser and pick two techniques (for example, "Valid Accounts" under Initial Access and "Command and Scripting Interpreter" under Execution). For each, read the description and write one sentence explaining what log evidence you would look for in a SIEM to catch it.
- [ ] Done: I can list the five incident response phases and map one technique to expected log evidence

## Day 70: Blue-team exercise: cause it, find it, report it
- **Learn:** A good blue teamer proves a detection works by generating the suspicious activity themselves and checking the alert fires. This exercise ties the whole week together: you create the noise (failed logins and a local port scan), search for it in your own SIEM, and write a short incident note like a real analyst would.
- **Do:** On your own machine, generate 10 failed logins (for example, bad SSH or RDP attempts to localhost) and run a port scan against localhost with Nmap. Make sure both get shipped into your Elastic Stack, then find them in Kibana with KQL, and write a one-paragraph incident note: what happened, when, from which source, and whether you consider it a true attack or a test.
- [ ] Done: I found my own failed logins and port scan in the SIEM and wrote a one-paragraph incident note
