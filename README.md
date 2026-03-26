<div align="center">
  <img src="https://img.shields.io/badge/SECURE--GATE-LDAP-111827?style=for-the-badge&logo=shield&logoColor=white" alt="Logo">
  
  <p align="center">
    <strong>Enterprise-Grade MFA Gateway for Active Directory & LDAP</strong>
  </p>

  <p align="center">
    <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
    <img src="https://img.shields.io/badge/Flask-2.0-000000?style=flat-square&logo=flask&logoColor=white" alt="Flask">
    <img src="https://img.shields.io/badge/MongoDB-4.4+-47A248?style=flat-square&logo=mongodb&logoColor=white" alt="MongoDB">
    <img src="https://img.shields.io/badge/Security-Hardened-success?style=flat-square" alt="Security">
  </p>
</div>

---

## 📖 Overview
**SecureGate-LDAP** is a hardened authentication proxy designed for the **Pearson BTEC IT System** curriculum. It introduces a **Zero-Trust** architecture to legacy infrastructure by requiring three independent factors: **Directory Credentials**, **reCAPTCHA Verification**, and **TOTP Tokens**.

---

## 💎 Project Advantages
This implementation offers several key improvements over standard authentication systems, specifically focusing on **Enterprise-Grade** security.

| Advantage | SecureGate-LDAP Solution | Standard Login System |
| :--- | :--- | :--- |
| **Credential Safety** | **MFA (TOTP)** ensures stolen passwords are useless without the physical device. | Vulnerable to single-point-of-failure if password is leaked. |
| **Bot Mitigation** | **Google reCAPTCHA v2** prevents automated "Credential Stuffing" attacks. | Open to brute-force scripts and automated bot logins. |
| **Identity Source** | **LDAP/Active Directory** integration allows for centralized corporate management. | Uses isolated local databases that are hard to sync at scale. |
| **Brute Force Guard** | **MongoDB Rate Limiting** locks accounts automatically after 5 failed attempts. | Often allows unlimited attempts, risking account takeover. |
| **Session Security** | **Hardened Headers (HSTS/CSP)** and Secure Cookies prevent MiTM attacks. | Often lacks modern security headers, leaving users at risk. |
| **Data Privacy** | **Environment Isolation** ensures no API keys or secrets are stored in the code. | Hardcoded secrets often lead to accidental data leaks on GitHub. |

---

---

## 🛠️ System Architecture

### 🛡️ The Triple-Lock Security Flow
1. **Identity Lock:** Validates credentials against **Active Directory** or **LDAP3**.
2. **Integrity Lock:** Uses **Google reCAPTCHA v2** to neutralize automated bot attacks.
3. **Ownership Lock:** Verifies a 6-digit **TOTP** token (Google Authenticator) generated from a unique Base32 secret stored in **MongoDB**.

---

## ✨ Features
* **Rate Limiting:** Automated account lockout after 5 failed attempts.
* **Cryptographic Safety:** Passwords hashed with `Bcrypt` (Salted).
* **Hardened Headers:** Protection against XSS, Clickjacking, and MiTM (HSTS).
* **Minimalist UI:** A clean, macOS-inspired interface designed for professional SaaS environments.

---

## 🚀 Installation & Setup

### ⌨️ Commands
```bash
# 1. Clone the repository
git clone [https://github.com/Yazan-Ayasrah/SecureGate-LDAP.git](https://github.com/Yazan-Ayasrah/SecureGate-LDAP.git)
cd SecureGate-LDAP

# 2. Install dependencies
pip install -r requirements.txt

# 3. Configure .env (See below)

# 4. Run the application
python app.py

