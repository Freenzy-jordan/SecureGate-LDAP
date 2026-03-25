# 🛡️ SecureGate-LDAP
### MFA-Integrated Web Application with Active Directory & LDAP

SecureGate-LDAP is a security-focused Flask application designed to demonstrate enterprise-grade authentication. It bridges traditional directory services (LDAP/AD) with modern security layers like **TOTP Multi-Factor Authentication** and **reCAPTCHA** bot protection.

---

## 🚀 Key Features
* **Dual-Layer Authentication:** Primary auth via LDAP/AD with secondary TOTP verification (Google Authenticator).
* **Brute-Force Protection:** Intelligent rate-limiting with account lockout (5 attempts / 5-minute cooldown).
* **Database Integration:** MongoDB backend for user metadata and login attempt tracking.
* **Hardened Security:** * CSRF Protection via Flask-WTF.
    * Secure Session Cookies (HttpOnly, SameSite, Secure).
    * Security Headers (HSTS, X-Frame-Options, X-Content-Type).
* **Bot Mitigation:** Integrated Google reCAPTCHA v2.

---

## 🛠️ Technical Stack
* **Language:** Python 3.x
* **Framework:** Flask
* **Database:** MongoDB
* **Security:** Bcrypt, PyOTP, LDAP3
* **Frontend:** HTML5, CSS3 (Minimalist Professional UI)

---

## ⚙️ Installation & Setup

### 1. Clone the repository
```bash
git clone [https://github.com/YourUsername/SecureGate-LDAP.git](https://github.com/YourUsername/SecureGate-LDAP.git)
cd SecureGate-LDAP
```

### 2. Install Dependencies
```bash
pip install flask flask-wtf pymongo bcrypt pyotp qrcode ldap3
```

### 3. Configure API Keys
#### Open app.py and replace the placeholder keys for reCAPTCHA:
```python
app.config['RECAPTCHA_PUBLIC_KEY'] = 'your_site_key'
app.config['RECAPTCHA_PRIVATE_KEY'] = 'your_secret_key'
```

### 4. Run the App
#### Open app.py and replace the placeholder keys for reCAPTCHA:
```bash
python app.py
```
