# SecureGate-LDAP
> **Enterprise-Grade Multi-Factor Authentication Bridge**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Flask](https://img.shields.io/badge/Framework-Flask-lightgrey.svg)](https://flask.palletsprojects.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🎯 Overview
SecureGate-LDAP is a high-security authentication gateway that integrates **Active Directory/LDAP** with modern **TOTP (MFA)** protocols. Designed for organizations requiring a secure bridge between legacy directory services and web-based applications.

## 🏗️ System Architecture
The application follows a "Zero-Trust" inspired authentication flow:



1. **Identity Verification:** Authenticates against LDAP/AD.
2. **Risk Assessment:** Google reCAPTCHA v2 validates the login attempt is human.
3. **MFA Challenge:** 6-digit TOTP verification via PyOTP (Google Authenticator compatible).
4. **Session Hardening:** Establishes an encrypted session with HSTS and secure cookie flags.

## 🛡️ Security Implementations
* **Rate Limiting:** Automatic account lockout after 5 failed attempts using MongoDB-backed tracking.
* **Header Hardening:** Implementation of `X-Frame-Options: DENY` and `Content-Security-Policy`.
* **Credential Safety:** Uses `Bcrypt` for local fallback hashing and `Secrets` for high-entropy session keys.

## 🚀 Deployment
1. **Setup Environment:**
   ```bash
   cp .env.example .env  # Configure your keys here
   pip install -r requirements.txt