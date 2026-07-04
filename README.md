# 🛡️ Windows 11 STIG Compliance Scan using Tenable (Lab Documentation)

This project demonstrates how to configure a Windows 11 virtual machine, set up local user accounts, and perform a compliance vulnerability scan using Tenable (Nessus) with DISA STIG benchmarks. The lab also compares scan results before and after disabling administrative accounts.

---

## 📌 Objective

- Deploy a Windows 11 VM for security testing
- Configure local users and groups
- Perform STIG compliance scans using Tenable
- Analyze vulnerabilities, compliance issues, and remediation steps
- Observe changes in scan results after disabling accounts

---

## 🖥️ Step 1: Create Windows 11 Virtual Machine

1. Create and boot a **Windows 11 Virtual Machine**
2. Log in to the system
3. Disable Windows Firewall for testing purposes:

   - Open `Windows Defender Firewall`
   - Turn off firewall for Domain, Private, and Public networks


---

## 👤 Step 2: Configure Local Users and Groups

### a) Create Administrator User

1. Open: Computer Management → Local Users and Groups → Users
2. 2. Right-click → **New User**
3. Set:
- Username: `administrator`
- Password: (your choice)
- Enable: *Password never expires*
4. Click **Create**

📷 **Fig.1: Creating Administrator User**

---

### b) Add User to Administrators Group

1. Open newly created user → Properties
2. Go to **Member Of** tab
3. Click **Add**
4. Enter:

Administrators

5. Click **OK → Apply**

📷 **Fig.3: Adding User to Administrators Group**

---

### c) Verify Group Membership

- Go to **Member Of tab**
- Confirm user is part of:

Administrators


📷 **Fig.4: Confirm Administrator Group Membership**

---

### d) Modify Guest Account

1. Select **Guest account**
2. Add it to:

Administrators group

3. Set Guest password to empty (blank)

📷 **Fig.5: Guest Account Configuration**

---

## 🔍 Step 3: Configure Tenable Scan Template

Create a new scan using **Advanced Network Scan**

---

### 🔧 Basic Settings

- Name: `Win-11-STIG-test`
- Start Remote Registry service during scan: ✅
- Enable administrative shares during scan: ✅
- Start Server service during scan: ✅

📷 **Fig.6: Basic Scan Settings**

---

### 🌐 Discovery Settings

- Ping the remote host: ✅
- Use fast network discovery: ✅
- TCP Port scanning: ✅

📷 **Fig.7: Discovery Settings**

---

### 🧪 Assessment Settings

- Perform thorough tests: ✅
- Only use credentials provided by the user: ❌ (UNCHECKED)

---

### 🔐 Credentials

Add Windows credentials:

- Username: `administrator`
- Password: `<your password>`

📷 **Fig.8: Credential Configuration**

---

### 📜 Compliance Settings

Add DISA STIG policy:

- Microsoft Windows 11 STIG v2r6 (or latest available)

📷 **Fig.9: STIG Compliance Policy Added**

---

### 🔌 Plugins Enabled

- General
- Policy Compliance
- Windows Compliance Checks
- Settings
- Windows
- Microsoft Bulletins
- User Management

📷 **Fig.10: Plugin Configuration**

---

## 🚀 Step 4: Run Initial Scan

1. Save scan template
2. Create a new scan using the template
3. Enter credentials again if required
4. Provide target IP address of VM
5. Launch scan

📷 **Fig.11: Scan Running**

---

## 📊 Step 5: Analyze Results

After scan completion, review:

- Vulnerabilities by Plugin
- Compliance Audit Results
- Failed STIG Controls
- Recommended Remediations

📷 **Fig.12: Scan Results Overview**

---

## 🔁 Step 6: Modify System & Re-run Scan

To observe changes in compliance results:

### Changes Applied:

1. Disable **Administrator account**
2. Disable **Guest account**

📷 **Fig.13: Disabled Accounts in Windows**

---

## 🔄 Step 7: Re-run Scan

1. Run the same Tenable scan again
2. Compare results with the previous scan

---

## 📈 Step 8: Result Comparison

Observe differences in:

- Number of vulnerabilities
- Compliance failures
- Authentication-related issues
- Privilege and access findings

📷 **Fig.14: Before vs After Scan Comparison**

---

## 🧠 Key Learnings

- Importance of privileged account management in STIG compliance
- Impact of disabled accounts on vulnerability scanning
- How Tenable detects misconfigurations in Windows systems
- Understanding compliance auditing vs vulnerability scanning

---

## 📌 Tools Used

- Windows 11 Pro VM
- Tenable Nessus (Advanced Network Scan)
- DISA STIG Benchmarks (Microsoft Windows 11 v2r6)

