# 🛡️ SecureGate-LDAP
> **An Enterprise-Grade Multi-Factor Authentication Bridge**

[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Framework-Flask-black?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![MongoDB](https://img.shields.io/badge/Database-MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

---

## 📖 Executive Summary
In modern enterprise environments, legacy **LDAP** and **Active Directory** systems are often vulnerable to credential harvesting and brute-force attacks. **SecureGate-LDAP** acts as a hardened proxy layer. It doesn't just check a password; it validates the **Humanity** (reCAPTCHA), the **Identity** (LDAP), and the **Presence** (TOTP) of the user before a session is ever created.



---

## 🛠️ Core Architecture & Logic

### 1. The Triple-Lock Auth Flow
The application follows a strict sequential verification process:
* **Layer 1: Bot Mitigation** 🤖
    * Utilizes Google reCAPTCHA v2 to ensure requests originate from a physical user, neutralizing automated credential stuffing.
* **Layer 2: Primary Directory Check** 🔑
    * Authenticates against `ldap3` servers. If LDAP is unavailable, the system safely falls back to a **Bcrypt-hashed** local database.
* **Layer 3: Cryptographic MFA** 📱
    * Generates a unique `Base32` secret for every user. Verification is handled via Time-based One-Time Passwords (TOTP) compatible with Google Authenticator.

### 2. Security Hardening (Deep Dive)
<details>
<summary><b>Click to view Technical Security Specs</b></summary>

* **Rate Limiting:** Implements a custom MongoDB-backed tracker. After 5 failed attempts, the account enters a `LOCKOUT_DURATION` state.
* **Session Integrity:** * `HttpOnly`: Prevents JavaScript from accessing session cookies (Mitigates XSS).
    * `SameSite=Lax`: Prevents cookies from being sent in cross-site requests (Mitigates CSRF).
* **Header Protection:** Enforces `Strict-Transport-Security` (HSTS) to ensure all traffic stays over HTTPS.
</details>

---

## 🎨 UI/UX Philosophy
Inspired by **macOS and SaaS minimalism**, the interface focuses on clarity and trust. 
* **Layout:** Centered 400px containers with 85% fluid application windows.
* **Visuals:** Clean borders, subtle shadows, and high-contrast primary charcoal (`#111827`) buttons.
* **Feedback:** Real-time flash messages for "Invalid OTP" or "Account Locked" to guide the user safely.

---

## 🚀 Deployment & Installation

### 📋 Prerequisites
* **Python:** Version 3.8 or higher.
* **Database:** MongoDB Compass or Atlas running locally.
* **Secrets:** A valid `.env` file (see below).

### ⌨️ Installation Steps
```bash
# 1. Clone the project
git clone [https://github.com/YourUsername/SecureGate-LDAP.git](https://github.com/YourUsername/SecureGate-LDAP.git)

# 2. Setup Virtual Environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install Dependencies
pip install -r requirements.txt

# 4. Run the Secure Server
python app.py