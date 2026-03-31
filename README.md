# Open Source Audit: VLC Media Player

**Course:** Open Source Software (NGMC)
**Student:** Kartikay Srivastava | **Registration:** 24BCG10021
**Slot:** E22 | **Date:** 31/03/2026

## Why VLC?

I chose VLC Media Player for this audit because of its awesome history starting as a student project at a French university. It also has an interesting dual-license setup (GPL for the app, LGPL for the core engine) and is one of the most downloaded open-source apps ever.

\---

## What's in this repo?

```text
oss-audit-24BCG10021/
│
├── README.md                          <-- You're reading this
│
├── scripts/
│   ├── script1\_system\_identity.sh     <-- Shows system info
│   ├── script2\_package\_inspector.sh   <-- Checks if a FOSS package is installed
│   ├── script3\_disk\_permission\_auditor.sh <-- Scans disk usage and permissions
│   ├── script4\_log\_analyzer.sh        <-- Searches log files for keywords
│   └── script5\_manifesto\_generator.sh <-- Generates an open-source manifesto
│
└── report/
    └── OSS\_Audit\_24BCG10021.pdf       <-- Final project report 
```

\---

## Script Breakdown

### 1\. System Identity Report (`script1\_system\_identity.sh`)

This script just prints out a welcome screen with my basic system info like the Linux distro, kernel version, who is logged in, uptime, and the current date/time. It also mentions the OS license. I used basic bash variables, command substitution (like `$(whoami)`), and `echo` to format the output nicely.

### 2\. Package Inspector (`script2\_package\_inspector.sh`)

I wrote this to check if a specific open-source package (like VLC) is installed. It automatically detects if you're using `rpm` (Fedora/RedHat) or `dpkg` (Ubuntu/Debian) to do the check. Then it grabs the package version and prints a quick philosophical note depending on the software. It makes heavy use of `if/else`, `case` statements, and piping data into `grep`.

### 3\. Disk \& Permission Auditor (`script3\_disk\_permission\_auditor.sh`)

This one loops through important directories (like `/etc`, `/var/log`, `/home`) and checks their permissions, owner, and size. It also specifically looks for VLC's plugin and config folders to see how much space they take up. It relies on standard `for` loops, `ls -ld`, `du`, and `awk` to chop up the output.

### 4\. Log Analyzer (`script4\_log\_analyzer.sh`)

A handy script to scan through a log file and count how many times a word (like `error`) shows up. If it finds matches, it prints the last 5 of them. I also added a retry loop so if the file is empty when you run it, it waits a bit and tries again before giving up. Takes command-line arguments (e.g., `$1` and `$2`).

### 5\. Manifesto Generator (`script5\_manifesto\_generator.sh`)

An interactive script! It asks you 3 quick questions using `read -p`. Based on what you type, it generates a personalized text file (`manifesto\_\[your\_username].txt`) with a short open-source philosophy statement. Shows off string appending and writing output to files.

\---

## How to run them

### What you need

* A Linux box (I tested this on Ubuntu).
* Bash shell.
* VLC installed (if you want Scripts 2 and 3 to show everything).

### Steps

1. **Clone the repo:**

```bash
   git clone https://github.com/kartikaysrivastava23/oss-audit-24BCG10021.git
   cd oss-audit-24BCG10021/scripts
   ```

2. **Give them execute permissions:**

```bash
   chmod +x \*.sh
   ```

3. **Run them!**

   * **Script 1:** `./script1\_system\_identity.sh`
   * **Script 2:** `./script2\_package\_inspector.sh` (Checks for VLC by default, but you can edit the script to check others).
   * **Script 3:** `./script3\_disk\_permission\_auditor.sh` (Might need `sudo` to see the sizes of some restricted folders like `/var/log`).
   * **Script 4:** `./script4\_log\_analyzer.sh /var/log/syslog error` (You can swap `error` for `WARNING` or whatever you're looking for).
   * **Script 5:** `./script5\_manifesto\_generator.sh` (Just answer the prompts).

\---

## Tools Used

All the scripts run on default Linux tools (`uname`, `date`, `whoami`, `grep`, `awk`, `cut`, `du`, `find`, `tail`, `cat`). No crazy external dependencies.
If you want to install VLC to get the full output for Scripts 2 and 3, run:
`sudo apt install vlc` (Ubuntu/Debian) or `sudo dnf install vlc` (Fedora).

\---

## License

I wrote these scripts for my academic coursework. They are released under the MIT License, so do whatever you want with them!

