# Phase 4: Python for Security

This phase turns you into someone who can write working Python scripts for real security tasks. Over 14 days you will go from the basics (variables, strings, loops) to practical security tools like log parsers, port scanners, and a small project you can push to your GitHub portfolio. Plan for about 1-2 hours per day.

## Day 29: Install Python, REPL, Variables, Data Types
- **Learn:** Python is an interpreted language, which means you can type code directly into the REPL (the interactive shell) and run it line by line. Variables store values like numbers, strings, and booleans, and you can print them or read user input.
- **Do:** Install Python 3, open a terminal, run `python3` to start the REPL, then create three variables (a string, an integer, a boolean), print them, and use `input()` to ask for your name and print a greeting.
- [ ] Done: you can run `python3`, create variables, and use `print()` and `input()` in the REPL

## Day 30: Strings, String Methods, f-strings
- **Learn:** Strings hold text, and Python gives you built-in methods like `.lower()`, `.strip()`, `.split()`, and `.replace()` to clean and reshape them. f-strings let you insert variables directly into text with the syntax `f"Hello {name}"`.
- **Do:** Write a script that takes a raw log line such as `"  ERROR: Failed LOGIN attempt from 192.168.1.5  "` and prints three cleaned versions: all lowercase, whitespace stripped, and split into a list of words. Print one summary line using an f-string that includes the word count and the IP address.
- [ ] Done: your script prints a cleaned log line and a formatted f-string summary

## Day 31: Lists, Dictionaries, Tuples, Sets
- **Learn:** Lists store ordered, changeable items; tuples are ordered but fixed; dictionaries map keys to values; sets store unique items with no duplicates. You will use all four when handling scan results, credentials, and log data.
- **Do:** Write a script that stores five open ports in a list, a host's details (IP, hostname, OS) in a dictionary, a scan range in a tuple, and uses a set to remove duplicate IPs from a list of ten IPs where three are repeated. Print each data structure.
- [ ] Done: your script builds and prints a list, dictionary, tuple, and a deduplicated set of IPs

## Day 32: Conditionals and Operators
- **Learn:** `if`, `elif`, and `else` let your program make decisions, and comparison operators (`==`, `!=`, `>`, `<`, `>=`, `<=`) combined with logical operators (`and`, `or`, `not`) build the conditions they test.
- **Do:** Write a port status checker: given a port number stored in a variable, print "well-known" for ports under 1024, "registered" for 1024-49151, "dynamic/private" for 49152-65535, and "invalid" for anything else. Test it with the values 22, 8080, 60000, and 99999.
- [ ] Done: your script classifies all four test ports into the correct ranges

## Day 33: Loops, break and continue
- **Learn:** `for` loops repeat over items in a list or a range, `while` loops repeat until a condition changes, and `break` exits a loop early while `continue` skips to the next iteration.
- **Do:** Write a script that loops through ports 1 to 100, skips even ports with `continue`, stops the loop with `break` when the port number passes 50, and prints each odd port it visits along with a final message showing where it stopped.
- [ ] Done: your script prints odd ports from 1 to 49 and stops cleanly after 50

## Day 34: Functions, Arguments, Return Values
- **Learn:** Functions group reusable code under a name, take inputs as arguments, and send results back with `return`. Good security scripts are built from small functions like `is_valid_ip()` or `check_port()` that you can test and reuse.
- **Do:** Write two functions: `is_private_ip(ip)` that returns True if the string starts with "192.168." or "10." (False otherwise), and `classify_port(port)` from Day 32 rewritten as a function that returns the category string. Call both with at least three test values each and print the results.
- [ ] Done: both functions return correct results for every test value you try

## Day 35: Modules, Imports, pip, Virtual Environments
- **Learn:** Modules are Python files you import to reuse code (like `os` or `re`), `pip` installs third-party packages, and a virtual environment (`venv`) keeps each project's packages isolated so they never clash.
- **Do:** Create a folder `sec-tools`, inside it run `python3 -m venv venv` and activate it, then run `pip install requests` and confirm with `pip list`. Write a script that imports `platform` and `datetime` and prints your OS name and the current date and time.
- [ ] Done: your virtual environment has requests installed and your script prints the OS and timestamp

## Day 36: Reading and Writing Files, Working with CSV
- **Learn:** The `open()` function with modes like `"r"`, `"w"`, and `"a"` reads, writes, and appends to text files, and the `csv` module reads and writes spreadsheet-style rows so you can store scan results in a portable format.
- **Do:** Write a script that creates `scan_results.csv` with a header row (host, port, status) and five rows of sample data, then reads the file back, counts how many rows have status "open", and prints the open ports as a list.
- [ ] Done: `scan_results.csv` exists with 5 data rows and your script reports the correct open-port count

## Day 37: Error Handling and Debugging Basics
- **Learn:** `try` and `except` catch errors like bad input or failed connections so your script keeps running instead of crashing. You can catch specific errors (like `ValueError` or `FileNotFoundError`) and print helpful messages instead of tracebacks.
- **Do:** Write a script that asks the user for a port number, wraps the `int()` conversion in try/except to handle non-numeric input, wraps reading `targets.txt` in try/except `FileNotFoundError`, and prints a friendly message in each failure case. Test it with the input `abc` and with a missing file.
- [ ] Done: both failure cases print friendly messages instead of crashing

## Day 38: Regular Expressions for Log Parsing
- **Learn:** Regular expressions (the `re` module) match text patterns, which makes them perfect for pulling IPs, timestamps, and status codes out of messy log lines. Key pieces are `\d` for digits, `\w` for word characters, `+` for one-or-more, and groups in parentheses.
- **Do:** Write a script using `re.findall()` with the pattern `r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"` to extract every IP address from five sample log lines you write yourself, then print each unique IP once.
- [ ] Done: your script extracts and prints each unique IP found in the sample log lines

## Day 39: The requests Library
- **Learn:** The `requests` library fetches web pages in a few lines: `requests.get(url)` returns a response object with `.status_code`, `.headers`, and `.text`. Checking status codes and headers is the starting point of web reconnaissance.
- **Do:** In your `sec-tools` virtual environment, write a script that sends GET requests to three websites of your choice, prints each URL with its status code, prints the `Server` and `Content-Type` headers for each, and saves the first 500 characters of one response body to `page_sample.txt`.
- [ ] Done: your script prints status codes and headers for three sites and saves a page sample

## Day 40: Sockets and a Simple Port Scanner
- **Learn:** The `socket` module opens raw TCP connections, and `socket.connect_ex((host, port))` returns 0 when a port is open, which is all you need to build a basic port scanner. Always scan only hosts you own or have written permission to test.
- **Do:** Write `port_scanner.py` with a function `scan_port(host, port)` that returns True when the port is open (use a 1-second timeout), then scan ports 20-100 on `127.0.0.1` and print which ones are open. Scan only your own machine.
- [ ] Done: your scanner runs against 127.0.0.1 and correctly lists the open ports it finds

## Day 41: Mini Project, Log File Analyzer
- **Learn:** A log analyzer combines everything so far: reading files, regular expressions, conditionals, dictionaries, and writing output. The goal is a script that flags suspicious lines like failed logins, so you can spot attacks in real logs.
- **Do:** Create `sample_auth.log` with at least 20 lines, including several `Failed password` lines from two different IPs. Write `log_analyzer.py` that reads the file, counts failed logins per IP in a dictionary, prints any IP with more than 3 failures as SUSPICIOUS, and writes the summary to `report.txt`.
- [ ] Done: `log_analyzer.py` prints the suspicious IPs and `report.txt` contains the per-IP counts

## Day 42: Review, Clean Up, Push to GitHub
- **Learn:** Reviewing your code means re-reading each script, adding comments, removing dead code, and making sure every file runs without errors. Pushing finished scripts to GitHub builds a portfolio that proves your skills.
- **Do:** Re-run every script from Days 29-41, add a short comment at the top of each explaining what it does, delete anything broken or unused, then create a GitHub repo named `python-security-scripts`, add a README describing each script in one line, and push all files.
- [ ] Done: all scripts run cleanly and are pushed to your GitHub repo with a README
