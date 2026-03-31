# Open Source Audit: VLC Media Player

This repository contains a series of shell scripts written for an academic audit of the VLC Media Player, as part of the Open Source Software (NGMC) course.

**Student:** Kartikay Srivastava (24BCG10021)

## Why VLC?

VLC Media Player was chosen for this audit due to its rich history as a student project that evolved into one of the most downloaded open-source applications worldwide. Its dual-license model (GPL for the application, LGPL for the core library) also presents an interesting case study in open-source strategy and philosophy.

## Repository Contents

This repository contains several shell scripts designed to audit a Linux system, with a specific focus on the VLC Media Player installation.

```text
.
├── README.md                      # This file
├── Project_Outline.md             # An outline for the final project report
├── manifesto.txt                  # An example output from script5
└── scripts/
    ├── script1_system_identity.sh     # Displays basic system and user information
    ├── script2_package_inspector.sh   # Checks if a FOSS package like VLC is installed
    ├── script3_disk_permission_auditor.sh # Audits disk usage and permissions of key directories
    ├── script4_log_analyzer.sh        # Searches log files for specific keywords
    └── script5_manifesto_generator.sh # Interactively generates a personal FOSS manifesto
```

## Script Descriptions

### 1. System Identity (`script1_system_identity.sh`)

This script generates a report that identifies the system. It displays the Linux distribution, kernel version, current user, home directory, system uptime, and the current date and time. It also provides a brief note on the GPL license used by the Linux kernel and VLC.

### 2. Package Inspector (`script2_package_inspector.sh`)

This script checks whether a specific package (defaulting to `vlc`) is installed on the system. It automatically detects the system's package manager (`dpkg` for Debian/Ubuntu or `rpm` for Fedora/RedHat) and displays the package version and description if found.

### 3. Disk & Permission Auditor (`script3_disk_permission_auditor.sh`)

This script audits important system directories (`/etc`, `/var/log`, `/home`, etc.), reporting their permissions, owner, and disk usage. It includes specific checks for VLC's plugin and configuration directories to analyze their footprint and permissions structure.

### 4. Log Analyzer (`script4_log_analyzer.sh`)

A utility to scan a given log file for a specified keyword (e.g., `error`, `warning`). The script counts the total occurrences of the keyword and displays the last five matching lines. It includes a retry mechanism in case the log file is initially empty.

### 5. Manifesto Generator (`script5_manifesto_generator.sh`)

An interactive script that prompts the user for their favorite open-source tool and their thoughts on software freedom. It then generates a personalized open-source "manifesto" and saves it to a text file named `manifesto_[your_username].txt`.

## How to Use

### Prerequisites

*   A Linux-based operating system (tested on Ubuntu).
*   Bash shell.
*   Standard command-line utilities (`grep`, `awk`, `du`, `cut`, etc.).
*   (Optional) VLC Media Player installed to get full output from all scripts.

### Execution Steps

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/kartikaysrivastava23/oss-audit-24bcg10021.git
    cd oss-audit-24bcg10021/scripts
    ```

2.  **Make the scripts executable:**
    ```bash
    chmod +x *.sh
    ```

3.  **Run the desired script:**

    *   **System Identity:**
        ```bash
        ./script1_system_identity.sh
        ```
    *   **Package Inspector:**
        ```bash
        ./script2_package_inspector.sh
        ```
    *   **Disk & Permission Auditor** (use `sudo` for full access):
        ```bash
        sudo ./script3_disk_permission_auditor.sh
        ```
    *   **Log Analyzer** (example with syslog):
        ```bash
        ./script4_log_analyzer.sh /var/log/syslog error
        ```
    *   **Manifesto Generator:**
        ```bash
        ./script5_manifesto_generator.sh
        ```

## Tools Used

All scripts are written in Bash and rely on standard, pre-installed Linux command-line tools. No external dependencies are required.

To install VLC for a complete audit experience, you can use your distribution's package manager:
*   **Debian/Ubuntu:** `sudo apt install vlc`
*   **Fedora/CentOS:** `sudo dnf install vlc`

## License

The scripts in this repository were created for academic purposes and are released under the **MIT License**. You are free to use, modify, and distribute them.
