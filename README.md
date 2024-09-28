# CyphyOS Post Installation Script

## Overview

This script is designed to help users transform any Debian-based installation into a CyphyOS-like environment. It automates the installation of essential tools, security configurations, hardware tools, and performance optimizations. CyphyOS is a specialized environment geared toward offensive security, hardware hacking, and anonymous operations, and this script bridges the gap between a vanilla Debian installation and a fully functional CyphyOS setup.

### Primary Features

1. **Tool Installation**: Install critical system and security tools required for CyphyOS.
2. **Anonymity Tools**: Configure `tor`, `proxychains`, and related tools to enable anonymous browsing and operations.
3. **Hardware Security Tools**: Install and configure hardware hacking tools like `usb2can`, `openocd`, and `flashrom`.
4. **System Hardening**: Apply robust security configurations, such as firewall rules (UFW), SSH hardening, and intrusion detection (Fail2Ban).
5. **Battery Optimization**: Use `TLP` to manage power consumption and enhance battery life, ideal for portable offensive security workstations.

---

## Table of Contents

- [Setup Requirements](#setup-requirements)
- [Installation and Usage](#installation-and-usage)
- [Script Features](#script-features)
  - [Tool Installation](#tool-installation)
  - [Hardware Security Tools](#hardware-security-tools)
  - [Anonymity Tools](#anonymity-tools)
  - [System Hardening](#system-hardening)
  - [TLP for Battery Optimization](#tlp-for-battery-optimization)
- [Detailed Explanations](#detailed-explanations)
  - [Why Each Tool Was Chosen](#why-each-tool-was-chosen)
- [Menu Options](#menu-options)
- [How It Works](#how-it-works)

---

## Setup Requirements

- **Debian 12.5.0 XFCE** (or higher version).
- Must be run as a **user with sudo privileges**.
- The `tools_list.conf` and `hardware_tools_list.conf` must be present in the same directory as the script.

**Configuration Files**:

- `tools_list.conf`: Contains general system tools required to set up a CyphyOS-like environment.
- `hardware_tools_list.conf`: Contains specialized tools for hardware hacking and security research.

---

## Installation and Usage

1. Clone or download the script and place it in the desired directory.

2. Ensure `tools_list.conf` and `hardware_tools_list.conf` are in the same directory as the script.

3. Make the script executable:
   
   bash
   
   Copy code
   
   `chmod +x cyphyos_post_install.sh`

4. Run the script:
   
   bash
   
   Copy code
   
   `./cyphyos_post_install.sh`

5. Use the interactive menu to install the necessary tools and configure the system.

---

## Script Features

### Tool Installation

The script installs a variety of essential system tools from `tools_list.conf`. These tools cover productivity, system monitoring, and security needs that are critical for transforming a Debian system into a CyphyOS-like environment.

**Example Tools**:

- **htop**: Process viewer for monitoring system performance.
- **ncdu**: Disk usage analyzer.
- **git**: Version control system for source code management.
- **keepassxc**: Secure password management tool.

### Hardware Security Tools

The script installs and configures hardware tools from `hardware_tools_list.conf`. These are crucial for embedded system analysis, reverse engineering, and firmware exploitation.

**Example Tools**:

- **usb2can-tools**: For CAN bus monitoring.
- **openocd**: On-chip debugger for hardware testing and debugging.
- **flashrom**: Tool for reading, writing, and verifying BIOS/firmware.

### Anonymity Tools

CyphyOS relies heavily on tools that ensure anonymity during offensive security activities. The script configures:

- **Tor**: A network for anonymizing internet traffic.
- **Proxychains**: Chains traffic through various proxies, including Tor, for secure browsing.
- **Tor Browser**: A secure browser designed for private browsing using the Tor network.

### System Hardening

To transform a Debian system into a secure CyphyOS setup, the script applies:

- **UFW**: Sets up a firewall with default-deny rules for incoming connections, allowing only necessary traffic like SSH.
- **Fail2Ban**: Bans IP addresses after repeated failed login attempts, preventing brute-force attacks.
- **SSH Hardening**: Disables root login and changes the default SSH port to increase security.

### TLP for Battery Optimization

CyphyOS often runs on laptops during offensive security operations. TLP optimizes power usage by dynamically adjusting CPU performance, power consumption, and other energy-saving configurations.

---

## Detailed Explanations

### Why Each Tool Was Chosen

1. **General System Tools**:
   
   - Tools like `htop`, `iotop`, `git`, and `keepassxc` are essential for managing system performance, development, and security.
   - `cherrytree` is included for note-taking, essential in research and documentation during security assessments.

2. **Hardware Security Tools**:
   
   - Tools such as `openocd`, `usb2can`, `libftdi1`, and `flashrom` are critical for interacting with hardware security systems, performing reverse engineering, and manipulating embedded firmware.

3. **Anonymity Tools**:
   
   - `tor` and `proxychains` ensure secure, anonymous browsing, critical during penetration testing or reconnaissance.

4. **System Hardening**:
   
   - The system hardening features ensure that the base Debian system is as secure as possible by limiting external attack vectors (via UFW) and protecting against brute-force attacks (via Fail2Ban).

5. **Battery Optimization**:
   
   - `TLP` ensures that laptops running CyphyOS can operate efficiently by managing power consumption, extending battery life during field operations.

---

## Menu Options

The script provides an interactive menu to perform various post-installation tasks, such as:

1. **Add User to Sudoers**: Adds the current user to the `sudoers` group, allowing them to execute privileged commands.
2. **Update Sources List**: Updates `/etc/apt/sources.list` to include `contrib`, `non-free`, and `non-free-firmware`, enabling access to a wider range of software repositories.
3. **Configure Greeter Settings**: Customizes the LightDM greeter to display user names at the login screen.
4. **System Update**: Runs `apt update` and `apt upgrade` to ensure the system is up-to-date.
5. **Install Tools**: Installs general tools from `tools_list.conf`.
6. **Install Hardware Tools**: Installs hardware security tools from `hardware_tools_list.conf`.
7. **Install TLP**: Optimizes battery usage by installing and configuring TLP.
8. **Install Anonymity Tools**: Sets up Tor, Proxychains, and Tor Browser for anonymous browsing and activities.
9. **System Hardening**: Applies firewall rules (UFW), SSH security configurations, and enables Fail2Ban for enhanced system security.
10. **Exit**: Exits the script.

---

## How It Works

- **Menu Driven**: The script operates via an interactive menu, allowing users to select specific tasks, such as installing tools or applying system hardening configurations.
- **Installation Checks**: For each tool in the lists, the script checks if it's already installed and skips it if necessary, ensuring idempotency.
- **Custom Whisker Menu Integration**: Any tools installed are added to a custom category within the Whisker menu for easy access.
- **Security Enhancements**: The script enforces basic security measures to ensure that the transformed system adheres to CyphyOS security standards.

---

## Future Work

- **Logging**: Implement logging to track script progress and installed tools.
- **Additional Anonymity Features**: Include VPN setup and additional proxy configurations.
- **Automated Update and Maintenance**: Add an option to regularly check and install updates.

---

### Authors & Contributors

- **Primary Developer**: [Your Name]
- **Contributors**: [List of Contributors]
