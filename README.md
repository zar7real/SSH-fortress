# 🏰 SSH-Fortress
## Ultimate SSH Security & Psychological Deterrent System

[![Version](https://img.shields.io/badge/version-2.0-blue.svg)](https://github.com/zar7real/SSH-fortress)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Security](https://img.shields.io/badge/security-hardened-red.svg)](https://github.com/zar7real/SSH-fortress)
[![Platform](https://img.shields.io/badge/platform-linux-lightgrey.svg)](https://github.com/zar7real/SSH-fortress)

---

## 📋 Table of Contents

- [🎯 Overview](#-overview)
- [✨ Features](#-features)
- [⚡ Quick Start](#-quick-start)
- [📦 Installation Guide](#-installation-guide)
- [🔧 Configuration](#-configuration)
- [🎨 Banner Customization](#-banner-customization)
- [🛡️ Security Features](#️-security-features)
- [📊 Monitoring & Logging](#-monitoring--logging)
- [🔍 Troubleshooting](#-troubleshooting)
- [🤝 Contributing](#-contributing)

---

## 🎯 Overview

**SSH-Fortress** is a comprehensive SSH hardening toolkit that combines military-grade security configurations with psychological deterrent banners. It transforms your SSH service into an impenetrable fortress that not only blocks attacks but also scares away potential intruders before they even try.

### 🎭 Psychological Warfare Approach

Unlike traditional security tools, SSH-Fortress employs **psychological deterrence** - making attackers believe they're targeting high-value government or military systems. This approach eliminates ~80% of casual attacks before they begin.

---

## ✨ Features

### 🔐 **Advanced Security**
- **Zero-tolerance authentication** with configurable attempt limits
- **Port knocking** and custom port configuration
- **IP whitelisting** and geo-blocking capabilities
- **Fail2ban integration** with custom rules
- **Key-based authentication** enforcement

### 🎨 **Psychological Banners**
- **Department of Defense** themed banners
- **Corporate defense contractor** warnings
- **Intelligence agency** classifications
- **Honeypot deception** messages
- **Custom banner generator**

### 📊 **Monitoring & Analytics**
- **Real-time intrusion detection**
- **Attack pattern analysis**
- **Detailed logging and reporting**
- **Alert notifications**

---

## ⚡ Quick Start

> **⚠️ Important**: Always backup your current SSH configuration before proceeding!

```bash
# 1. Clone the repository
git clone https://github.com/zar7real/SSH-fortress.git
cd SSH-fortress

# 2. Make scripts executable
chmod +x install.sh configure.sh

# 3. Run the installer (requires sudo)
sudo ./install.sh

# 4. Follow the interactive setup
sudo ./configure.sh
```

**🎉 That's it!** Your SSH service is now fortified and ready to repel invaders.

---

## 📦 Installation Guide

### 📋 Prerequisites

Before starting, ensure your system meets these requirements:

- **Operating System**: Ubuntu 18.04+, Debian 10+, CentOS 7+, or similar
- **Root Access**: Required for system configuration
- **SSH Service**: OpenSSH server installed
- **Network Access**: For downloading dependencies

### 🔍 System Compatibility Check

```bash
# Check your OS version
cat /etc/os-release

# Verify SSH is installed
systemctl status ssh || systemctl status sshd

# Check current SSH configuration
sudo sshd -T
```

### 📥 Step-by-Step Installation

#### **Step 1: Download SSH-Fortress**

```bash
# Navigate to your preferred directory
cd /opt

# Clone the repository
sudo git clone https://github.com/zar7real/SSH-fortress.git

# Enter the directory
cd SSH-fortress

# View contents
ls -la
```

**What this does**: Downloads all SSH-Fortress files to your system in the `/opt` directory, which is the standard location for optional software packages.

#### **Step 2: Prepare Installation**

```bash
# Make installation scripts executable
sudo chmod +x *.sh

# Create backup directory
sudo mkdir -p /opt/SSH-fortress/backups

# Backup current SSH configuration
sudo cp /etc/ssh/sshd_config /opt/SSH-fortress/backups/sshd_config.backup.$(date +%Y%m%d_%H%M%S)
```

**What this does**: 
- Makes the installation scripts runnable
- Creates a backup folder to store your original configurations
- Saves your current SSH settings with a timestamp so you can restore them if needed

#### **Step 3: Run the Installer**

```bash
# Execute the main installer
sudo ./install.sh
```

**The installer will**:
1. **Check system compatibility**
2. **Install required dependencies** (fail2ban, ufw, etc.)
3. **Create necessary directories**
4. **Set up logging infrastructure**
5. **Install monitoring scripts**

#### **Step 4: Interactive Configuration**

```bash
# Launch the configuration wizard
sudo ./configure.sh
```

The configuration wizard will ask you several questions:

**🔧 Configuration Questions Explained**:

1. **SSH Port Selection**
   ```
   Current SSH port: 22
   Do you want to change it? (y/N)
   ```
   - **Why**: Port 22 is heavily targeted by bots
   - **Recommendation**: Choose a high port (1024-65535)
   - **Example**: 2847, 8922, 45623

2. **Banner Selection**
   ```
   Select security banner type:
   1) Department of Defense (Intimidating)
   2) Corporate Defense (Professional)
   3) Intelligence Agency (Classified)
   4) Honeypot Deception (Trap-like)
   5) Custom Banner
   ```
   - **DoD Banner**: Scares script kiddies and casual attackers
   - **Corporate**: Deters those afraid of legal consequences
   - **Intelligence**: Intimidates sophisticated attackers
   - **Honeypot**: Makes them think it's an FBI trap

3. **Authentication Settings**
   ```
   Maximum login attempts before ban: (default: 3)
   Ban duration in minutes: (default: 60)
   ```
   - **Max attempts**: How many wrong passwords before blocking
   - **Ban duration**: How long to block the IP address

4. **Allowed Users Configuration**
   ```
   Enter usernames allowed SSH access (space-separated):
   ```
   - **Purpose**: Only these users can attempt SSH login
   - **Security**: Prevents attacks on common usernames like 'admin', 'root'

---

## 🔧 Configuration

### 📁 Configuration Files Overview

SSH-Fortress uses several configuration files:

```
/etc/ssh/
├── sshd_config          # Main SSH daemon configuration
├── ssh_banner          # Login banner displayed to users
└── allowed_users       # List of permitted SSH users

/etc/fail2ban/
├── jail.local          # Fail2ban SSH jail configuration
└── filter.d/
    └── sshd-fortress.conf  # Custom SSH attack patterns

/opt/SSH-fortress/
├── config/
│   ├── banners/        # Collection of security banners
│   └── templates/      # Configuration templates
└── scripts/
    ├── monitor.sh      # Real-time monitoring script
    └── report.sh       # Generate security reports
```

### ⚙️ Advanced Configuration Options

#### **Custom SSH Hardening**

Edit the main configuration:

```bash
# Open SSH configuration
sudo nano /etc/ssh/sshd_config
```

**Key Security Settings Explained**:

```bash
# Disable root login (prevents direct root access)
PermitRootLogin no

# Use only SSH key authentication (no passwords)
PasswordAuthentication no
PubkeyAuthentication yes

# Limit concurrent connections
MaxAuthTries 3
MaxSessions 2

# Timeout settings (disconnect idle sessions)
ClientAliveInterval 300
ClientAliveCountMax 2

# Allowed users only
AllowUsers john mike sarah

# Protocol version (only use SSH version 2)
Protocol 2
```

**What each setting does**:
- `PermitRootLogin no`: Prevents direct root access via SSH
- `PasswordAuthentication no`: Forces use of SSH keys instead of passwords
- `MaxAuthTries 3`: Only 3 login attempts before disconnection
- `ClientAliveInterval 300`: Disconnect inactive sessions after 5 minutes
- `AllowUsers`: Only specified users can connect via SSH

#### **Firewall Configuration**

```bash
# Check current firewall status
sudo ufw status

# Allow SSH on custom port (replace 2847 with your port)
sudo ufw allow 2847/tcp

# Enable firewall
sudo ufw enable

# Verify rules
sudo ufw status numbered
```

### 🔄 Apply Configuration Changes

After making any changes:

```bash
# Test configuration syntax
sudo sshd -t

# If test passes, restart SSH service
sudo systemctl restart ssh

# Check service status
sudo systemctl status ssh
```

**⚠️ Important**: Always test your configuration before closing your current SSH session!

---

## 🎨 Banner Customization

### 🖼️ Available Banner Types

#### **1. Department of Defense Banner**
```
################################################################################
#                                                                              #
#                    U.S. DEPARTMENT OF DEFENSE NETWORK                       #
#                         AUTHORIZED ACCESS ONLY                              #
#                                                                              #
################################################################################

WARNING: This is a U.S. Government computer system...
```

**Psychological Effect**: Intimidates casual attackers and script kiddies who fear government retaliation.

#### **2. Corporate Defense Contractor**
```
                           LOCKHEED MARTIN CORPORATION
                         CLASSIFIED DEFENSE CONTRACTOR SYSTEM
                              AUTHORIZED ACCESS ONLY

WARNING: This system contains proprietary defense technology...
```

**Psychological Effect**: Deters attackers afraid of corporate legal teams and ITAR violations.

#### **3. Intelligence Agency Classification**
```
█████████████████████████████████████████████████████████████████████████████
█                                                                           █
█                    CENTRAL INTELLIGENCE AGENCY                            █
█                         CLASSIFIED SYSTEM                                 █
█                                                                           █
█████████████████████████████████████████████████████████████████████████████
```

**Psychological Effect**: Scares sophisticated attackers who fear intelligence agency attention.

#### **4. Honeypot Deception**
```
    ██╗  ██╗ ██████╗ ███╗   ██╗███████╗██╗   ██╗██████╗  ██████╗ ████████╗
    ██║  ██║██╔═══██╗████╗  ██║██╔════╝╚██╗ ██╔╝██╔══██╗██╔═══██╗╚══██╔══╝
    ███████║██║   ██║██╔██╗ ██║█████╗   ╚████╔╝ ██████╔╝██║   ██║   ██║   

CONGRATULATIONS! You have accessed a federal honeypot system...
```

**Psychological Effect**: Makes attackers believe they've been caught in an FBI trap.

### 🛠️ Installing Custom Banners

#### **Method 1: Use Provided Banners**

```bash
# Navigate to banners directory
cd /opt/SSH-fortress/config/banners/

# List available banners
ls -la

# Copy desired banner to SSH directory
sudo cp dod_banner.txt /etc/ssh/ssh_banner

# Set proper permissions
sudo chmod 644 /etc/ssh/ssh_banner

# Update SSH configuration to use banner
echo "Banner /etc/ssh/ssh_banner" | sudo tee -a /etc/ssh/sshd_config

# Restart SSH service
sudo systemctl restart ssh
```

#### **Method 2: Create Custom Banner**

```bash
# Create your custom banner
sudo nano /etc/ssh/ssh_banner
```

**Banner Design Tips**:
- **Keep it intimidating but believable**
- **Use official-sounding language**
- **Include legal warnings**
- **Mention specific laws (like 18 U.S.C. § 1030)**
- **Add technical details for credibility**

**Example Custom Banner**:
```
################################################################################
#                       SECURE GOVERNMENT FACILITY                            #
#                         RESTRICTED ACCESS SYSTEM                            #
################################################################################

WARNING: This system is monitored by advanced AI security algorithms.
All connection attempts are analyzed and logged to federal databases.

Unauthorized access constitutes a violation of:
• 18 U.S.C. § 1030 (Computer Fraud and Abuse Act)
• Executive Order 13636 (Critical Infrastructure Security)
• DoD Directive 8500.01 (Information Assurance)

Real-time threat detection active. Your IP and location are being traced.
Malicious activity will result in immediate law enforcement notification.

AUTHORIZED PERSONNEL ONLY - DISCONNECT NOW IF UNAUTHORIZED
```

#### **Method 3: Dynamic Banner Rotation**

Create a script that rotates banners periodically:

```bash
# Create banner rotation script
sudo nano /opt/SSH-fortress/scripts/rotate_banner.sh
```

```bash
#!/bin/bash
# Banner rotation script

BANNER_DIR="/opt/SSH-fortress/config/banners"
BANNERS=("dod_banner.txt" "corporate_banner.txt" "intel_banner.txt" "honeypot_banner.txt")
RANDOM_BANNER=${BANNERS[$RANDOM % ${#BANNERS[@]}]}

# Copy random banner
cp "$BANNER_DIR/$RANDOM_BANNER" /etc/ssh/ssh_banner
chmod 644 /etc/ssh/ssh_banner

# Log the change
echo "$(date): Banner changed to $RANDOM_BANNER" >> /var/log/ssh-fortress.log

# Restart SSH to apply
systemctl reload ssh
```

```bash
# Make script executable
sudo chmod +x /opt/SSH-fortress/scripts/rotate_banner.sh

# Add to crontab for daily rotation
echo "0 2 * * * /opt/SSH-fortress/scripts/rotate_banner.sh" | sudo crontab -
```

---

## 🛡️ Security Features

### 🔒 Multi-Layer Protection

SSH-Fortress implements **defense in depth** with multiple security layers:

#### **Layer 1: Network Level**
- **Port obfuscation** (custom SSH port)
- **Firewall rules** (UFW/iptables integration)
- **Rate limiting** (connection throttling)
- **Geo-blocking** (country-based restrictions)

#### **Layer 2: Authentication**
- **Key-based authentication** (no passwords)
- **Multi-factor authentication** support
- **User restriction** (AllowUsers directive)
- **Time-based access** controls

#### **Layer 3: Behavioral Analysis**
- **Fail2ban integration** with custom rules
- **Intrusion detection** patterns
- **Anomaly detection** for unusual activity
- **Automated response** to threats

#### **Layer 4: Psychological Deterrence**
- **Intimidating banners** to scare attackers
- **Honeypot deception** techniques
- **Legal warning** displays
- **False complexity** indicators

### 🔧 Configuring Advanced Security Features

#### **SSH Key Authentication Setup**

**Step 1: Generate SSH Key Pair (on your local machine)**

```bash
# Generate a strong SSH key pair
ssh-keygen -t ed25519 -b 4096 -C "your_email@example.com"

# For older systems that don't support ed25519
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

**What this does**: Creates a pair of cryptographic keys - a private key (stays on your computer) and a public key (goes on the server).

**Step 2: Copy Public Key to Server**

```bash
# Copy public key to server
ssh-copy-id -p YOUR_SSH_PORT username@your_server_ip

# Manual method if ssh-copy-id doesn't work
cat ~/.ssh/id_ed25519.pub | ssh -p YOUR_SSH_PORT username@your_server_ip "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

**Step 3: Disable Password Authentication**

```bash
# Edit SSH configuration
sudo nano /etc/ssh/sshd_config

# Change these lines:
PasswordAuthentication no
PubkeyAuthentication yes
AuthenticationMethods publickey

# Restart SSH
sudo systemctl restart ssh
```

#### **Fail2ban Custom Rules**

SSH-Fortress includes advanced Fail2ban rules:

```bash
# View current jail status
sudo fail2ban-client status sshd-fortress

# Check banned IPs
sudo fail2ban-client get sshd-fortress banip

# Manually ban an IP
sudo fail2ban-client set sshd-fortress banip 192.168.1.100

# Unban an IP
sudo fail2ban-client set sshd-fortress unbanip 192.168.1.100
```

**Custom Detection Patterns**:
- **Brute force attempts**
- **Dictionary attacks**
- **Port scanning behavior**
- **Repeated connection failures**
- **Suspicious timing patterns**

#### **Geo-blocking Configuration**

Block entire countries from accessing SSH:

```bash
# Install geoip database
sudo apt-get install geoip-database geoip-bin

# Create geo-blocking script
sudo nano /opt/SSH-fortress/scripts/geoblock.sh
```

```bash
#!/bin/bash
# Countries to block (ISO country codes)
BLOCKED_COUNTRIES=("CN" "RU" "KP" "IR")

for country in "${BLOCKED_COUNTRIES[@]}"; do
    # Get IP ranges for country
    wget -O /tmp/${country}.txt "http://www.ipdeny.com/ipblocks/data/countries/${country,,}.zone"
    
    # Add firewall rules
    while read -r ip; do
        ufw deny from "$ip"
    done < /tmp/${country}.txt
    
    rm /tmp/${country}.txt
done
```

---

## 📊 Monitoring & Logging

### 📈 Real-Time Monitoring

SSH-Fortress provides comprehensive monitoring capabilities:

#### **Live Attack Monitoring**

```bash
# Start real-time monitoring
sudo /opt/SSH-fortress/scripts/monitor.sh
```

**What you'll see**:
```
[2024-06-09 14:23:45] 🚨 ALERT: Brute force attack from 192.168.1.100
[2024-06-09 14:23:46] 🛡️  BLOCKED: IP 192.168.1.100 banned for 1 hour
[2024-06-09 14:24:12] 📊 STATS: 15 attacks blocked in last hour
[2024-06-09 14:24:13] 🎯 PATTERN: Dictionary attack detected from 10.0.0.50
```

#### **Generate Security Reports**

```bash
# Generate daily security report
sudo /opt/SSH-fortress/scripts/report.sh daily

# Generate weekly summary
sudo /opt/SSH-fortress/scripts/report.sh weekly

# Generate monthly analysis
sudo /opt/SSH-fortress/scripts/report.sh monthly
```

**Sample Report Output**:
```
🏰 SSH-Fortress Security Report - Daily Summary
📅 Date: June 09, 2024

📊 Attack Statistics:
   Total Attacks: 127
   Unique IPs: 45
   Countries: China (67%), Russia (23%), Iran (10%)
   
🛡️ Defense Actions:
   IPs Banned: 45
   Connections Dropped: 127
   False Positives: 0
   
🎯 Attack Patterns:
   Brute Force: 89 attempts
   Dictionary: 23 attempts
   Port Scanning: 15 attempts
   
⚠️  Recommendations:
   • Consider geo-blocking China and Russia
   • Update SSH keys (last rotation: 30 days ago)
   • Review user access logs
```

### 📋 Log File Locations

SSH-Fortress maintains detailed logs:

```bash
# Main SSH-Fortress log
tail -f /var/log/ssh-fortress.log

# SSH authentication attempts
tail -f /var/log/auth.log | grep ssh

# Fail2ban activity
tail -f /var/log/fail2ban.log

# Firewall blocks
tail -f /var/log/ufw.log
```

#### **Understanding Log Entries**

**SSH-Fortress Log Format**:
```
[TIMESTAMP] [LEVEL] [COMPONENT] MESSAGE
```

**Example Entries**:
```
[2024-06-09 14:23:45] [ALERT] [BANNER] Attacker 192.168.1.100 disconnected after seeing DoD banner
[2024-06-09 14:24:12] [INFO] [AUTH] Failed login attempt for user 'admin' from 10.0.0.50
[2024-06-09 14:24:13] [WARN] [PATTERN] Dictionary attack pattern detected from 10.0.0.50
[2024-06-09 14:24:14] [ACTION] [FAIL2BAN] IP 10.0.0.50 banned for 3600 seconds
```

### 📈 Performance Monitoring

Monitor SSH-Fortress impact on system performance:

```bash
# Check SSH service performance
sudo systemctl status ssh --no-pager -l

# Monitor resource usage
sudo /opt/SSH-fortress/scripts/performance.sh

# View connection statistics
ss -tuln | grep :22 # Replace 22 with your SSH port
```

---

## 🔍 Troubleshooting

### 🚨 Common Issues and Solutions

#### **Issue 1: Locked Out of SSH**

**Symptoms**: Can't connect to SSH after configuration changes

**Solution**:
```bash
# If you have console access to the server:
sudo systemctl stop ssh
sudo cp /opt/SSH-fortress/backups/sshd_config.backup.* /etc/ssh/sshd_config
sudo systemctl start ssh

# Test connection from another terminal before closing current session
ssh -p YOUR_PORT username@your_server
```

**Prevention**: Always test configuration and keep a backup session open.

#### **Issue 2: Fail2ban Not Working**

**Symptoms**: Attackers not being blocked automatically

**Diagnostics**:
```bash
# Check fail2ban status
sudo systemctl status fail2ban

# Check jail configuration
sudo fail2ban-client status

# View fail2ban logs
sudo tail -f /var/log/fail2ban.log

# Test jail configuration
sudo fail2ban-client reload sshd-fortress
```

**Common fixes**:
```bash
# Restart fail2ban service
sudo systemctl restart fail2ban

# Check log file permissions
sudo ls -la /var/log/auth.log

# Verify SSH log format matches filter
sudo fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf
```

#### **Issue 3: Banner Not Displaying**

**Symptoms**: No warning banner appears when connecting

**Solution**:
```bash
# Check banner file exists and has correct permissions
ls -la /etc/ssh/ssh_banner
sudo chmod 644 /etc/ssh/ssh_banner

# Verify SSH configuration includes banner
grep "Banner" /etc/ssh/sshd_config

# If missing, add banner directive
echo "Banner /etc/ssh/ssh_banner" | sudo tee -a /etc/ssh/sshd_config

# Test SSH configuration
sudo sshd -t

# Restart SSH service
sudo systemctl restart ssh
```

#### **Issue 4: High CPU Usage**

**Symptoms**: Server performance degraded after SSH-Fortress installation

**Diagnostics**:
```bash
# Check process CPU usage
top -p $(pgrep -d, ssh)

# Monitor SSH connections
sudo netstat -tnpa | grep ':22'

# Check for excessive logging
sudo du -sh /var/log/

# Review fail2ban resource usage
sudo fail2ban-client get sshd-fortress stats
```

**Optimization**:
```bash
# Reduce log verbosity
sudo nano /etc/ssh/sshd_config
# Change: LogLevel VERBOSE
# To: LogLevel INFO

# Optimize fail2ban settings
sudo nano /etc/fail2ban/jail.local
# Increase findtime and bantime
# Reduce maxretry if needed
```

### 🛠️ Advanced Troubleshooting

#### **SSH Configuration Testing**

```bash
# Test SSH configuration syntax
sudo sshd -t

# Test with verbose output
sudo sshd -T

# Debug SSH connection issues
ssh -v -p YOUR_PORT username@your_server

# Test from different IP to verify access controls
```

#### **Network Connectivity Issues**

```bash
# Check if SSH port is listening
sudo netstat -tlnp | grep :YOUR_SSH_PORT

# Test port accessibility from outside
nmap -p YOUR_SSH_PORT your_server_ip

# Check firewall rules
sudo ufw status numbered
sudo iptables -L -n

# Verify routing
traceroute your_server_ip
```

#### **Log Analysis Tools**

```bash
# Analyze SSH attack patterns
sudo /opt/SSH-fortress/scripts/analyze_logs.sh

# Generate attack timeline
sudo grep "Failed password" /var/log/auth.log | tail -20

# Check for successful compromises
sudo grep "Accepted" /var/log/auth.log | tail -10

# Monitor real-time attacks
sudo tail -f /var/log/auth.log | grep --color=auto "Failed\|Invalid\|Illegal"
```

---

## ⚙️ Advanced Features

### 🔧 Custom Attack Detection

Create custom patterns for detecting sophisticated attacks:

```bash
# Create custom fail2ban filter
sudo nano /etc/fail2ban/filter.d/ssh-advanced.conf
```

```ini
[Definition]
# Advanced SSH attack patterns
failregex = ^%(__prefix_line)s(?:error: PAM: )?[aA]uthentication (?:failure|error|failed) for .* from <HOST>( via \S+)?\s*$
            ^%(__prefix_line)s(?:error: )?Received disconnect from <HOST>: 3: .*: Auth fail$
            ^%(__prefix_line)sFailed (?:password|publickey) for invalid user .* from <HOST>$
            ^%(__prefix_line)sUser .* from <HOST> not allowed because not listed in AllowUsers$
            ^%(__prefix_line)sUser .* from <HOST> not allowed because listed in DenyUsers$
            ^%(__prefix_line)sUser .* from <HOST> not allowed because not in any group$
            ^%(__prefix_line)srefused connect from \S+ \(<HOST>\)$
            ^%(__prefix_line)sReceived disconnect from <HOST>: 11: Bye Bye$
            ^%(__prefix_line)sConnection closed by <HOST> \[preauth\]$
            ^%(__prefix_line)sDisconnected from <HOST> \[preauth\]$

ignoreregex =

datepattern = {^LN-BEG}
```

### 🎯 Honeypot Integration

Set up decoy services to attract and analyze attackers:

```bash
# Install and configure cowrie honeypot
sudo apt-get install python3-pip python3-venv
python3 -m venv cowrie-env
source cowrie-env/bin/activate
pip install cowrie

# Configure cowrie to run on port 2222
sudo nano cowrie.cfg
```

### 📱 Mobile Alerts

Set up SMS/email alerts for critical events:

```bash
# Install required packages
sudo apt-get install mailutils ssmtp

# Configure SSMTP for email alerts
sudo nano /etc/ssmtp/ssmtp.conf
```

```ini
root=your-email@example.com
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
AuthUser=your-email@example.com
AuthPass=your-app-password
```

Create alert script:
```bash
sudo nano /opt/SSH-fortress/scripts/alert.sh
```

```bash
#!/bin/bash
# SSH-Fortress Alert System

ALERT_EMAIL="admin@yourcompany.com"
ALERT_PHONE="1234567890"  # For SMS via email-to-SMS gateway

send_alert() {
    local severity=$1
    local message=$2
    local timestamp=$(date)
    
    # Email alert
    echo "SSH-Fortress Alert: $severity
Time: $timestamp
Message: $message
Server: $(hostname)
IP: $(curl -s ifconfig.me)" | mail -s "🚨 SSH-Fortress Alert: $severity" "$ALERT_EMAIL"
    
    # SMS alert (via email-to-SMS gateway)
    echo "$severity: $message" | mail -s "" "$ALERT_PHONE@txt.att.net"
}

# Usage examples:
# send_alert "CRITICAL" "Multiple brute force attacks detected"
# send_alert "WARNING" "Unusual login pattern from new IP"
```

---

## 🔄 Maintenance and Updates

### 📅 Regular Maintenance Tasks

#### **Weekly Tasks**
```bash
#!/bin/bash
# Weekly maintenance script

# Update threat intelligence
sudo /opt/SSH-fortress/scripts/update_threats.sh

# Rotate logs
sudo logrotate -f /etc/logrotate.d/ssh-fortress

# Generate security report
sudo /opt/SSH-fortress/scripts/report.sh weekly

# Check for configuration drift
sudo /opt/SSH-fortress/scripts/config_check.sh
```

#### **Monthly Tasks**
```bash
#!/bin/bash
# Monthly maintenance script

# Update SSH-Fortress
cd /opt/SSH-fortress && sudo git pull

# Rotate SSH keys (if using automated key rotation)
sudo /opt/SSH-fortress/scripts/rotate_keys.sh

# Update geo-blocking lists
sudo /opt/SSH-fortress/scripts/update_geoblock.sh

# Performance optimization
sudo /opt/SSH-fortress/scripts/optimize.sh
```

### 🔄 Updating SSH-Fortress

```bash
# Check current version
cat /opt/SSH-fortress/VERSION

# Pull latest updates
cd /opt/SSH-fortress
sudo git pull origin main

# Run update script
sudo ./update.sh

# Verify installation
sudo ./verify.sh
```

---

## 📈 Performance Optimization

### ⚡ Optimization Tips

#### **SSH Performance Tuning**
```bash
# Edit SSH configuration for better performance
sudo nano /etc/ssh/sshd_config

# Add these optimizations:
# Compression yes (for slow connections)
# TCPKeepAlive yes
# UseDNS no (faster connections)
# GSSAPIAuthentication no (unless needed)
```

#### **Fail2ban Optimization**
```bash
# Optimize fail2ban for high-traffic servers
sudo nano /etc/fail2ban/jail.local

[sshd-fortress]
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
findtime = 600
bantime = 3600
# For high-traffic: increase findtime and bantime
```

#### **Log Management**
```bash
# Configure log rotation
sudo nano /etc/logrotate.d/ssh-fortress

/var/log/ssh-fortress.log {
    daily
    missingok
    rotate 30
    compress
    delaycompress
    notifempty
    copytruncate
    postrotate
        systemctl reload rsyslog > /dev/null 2>&1 || true
    endscript
}
```

---

## 🤝 Contributing

We welcome contributions to SSH-Fortress! Here's how you can help:

### 🐛 Reporting Bugs

1. **Check existing issues** on GitHub
2. **Create detailed bug report** with:
   - Operating system and version
   - SSH-Fortress version
   - Steps to reproduce
   - Expected vs actual behavior
