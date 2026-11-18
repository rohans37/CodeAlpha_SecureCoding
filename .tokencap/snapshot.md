<!-- TokenCap v1.6 Savings: baseline 16,770 tok → actual 6,056 tok (63.9% saved) -->
# AI ENTRY POINT

This repository has been indexed by TokenCap.

Before analyzing files, read:

.tokencap/agent/START_HERE.md

Use:

- .tokencap/agent/agent-pack.md
- .tokencap/agent/allowed-context.json
- .tokencap/agent/context-manifest.json

Do not rediscover the repository from scratch.

---

# TokenCap Snapshot

| Field | Value |
| --- | --- |
| Generated | 2026-11-18T04:53:25.067Z |
| Workspace | c:\Users\Rohan\Downloads\Intern\CodeAlpha_Basic Network Sniffer\CodeAlpha_Secure Coding Review |
| Profile | balanced |
| Selected files | 6 |
| Source bytes | 52146 |
| Estimated source tokens | 12388 |

## Read First

This file is a compressed coding-session handoff. Read it before editing, then inspect the referenced files directly. Prefer the live repository over this snapshot when there is a conflict.

## TokenCap Intelligence Files

- TOKENCAP_GRAPH.md — Project dependency and architecture graph *(JS/TS projects only)*
- TOKENCAP_MEMORY.md — Developer notes, current task, constraints, and context memory

## Handoff Summary

| Field | Value |
| --- | --- |
| Read order | README.md > requirements.txt > bandit_report.txt > Code_Review_Report.md > secure_app.py |
| Primary anchors | README.md, requirements.txt, bandit_report.txt |
| Changed files | 1 |
| TODO notes | 0 |
| File budget used | 7% |
| Source budget used | 24% |
| Token estimate | 12388 |
| Contents mode | enabled |

## Handoff Guidelines

- Preserve user changes; avoid reverting unrelated work.
- Start with changed files and files marked `high-signal` in the manifest.
- Treat the Git diff as intent and verify changes in source files.
- Update this snapshot after meaningful edits or before handing off.

## Git Snapshot

| Field | Value |
| --- | --- |
| Branch | main |
| Git root | C:/Users/Rohan/Downloads/Intern/CodeAlpha_Basic Network Sniffer/CodeAlpha_Secure Coding Review |

Recent commits:
```text
6648109 feat: Added demonstrations screenshots
4358269 Feat: added simple GUI for both apps
96d7b72 Add Bandit security analysis report
245b857 Remove bandit report from repository
b5a26ec first commit
eedebdc first commit
```

Status:
```text
 M README.md
```

## Project Map

```text
Code_Review_Report.md
README.md
bandit_report.txt
requirements.txt
secure_app.py
vulnerable_app.py
```

## File Manifest

| File | Bytes | Score | Why |
| --- | ---: | ---: | --- |
| README.md | 4870 | 225 | changed, project-metadata, high-signal-doc |
| requirements.txt | 31 | 70 | project-metadata |
| bandit_report.txt | 5214 | 0 | context |
| Code_Review_Report.md | 8353 | 0 | context |
| secure_app.py | 18891 | -1 | context |
| vulnerable_app.py | 14787 | -1 | context |

## Changed Files

-  M README.md

## Git Diff Snippets

### Unstaged Changes Diff

```diff
diff --git a/README.md b/README.md
index 24f5eb0..7e924d2 100644
--- a/README.md
+++ b/README.md
@@ -86,7 +86,7 @@ Ensure you have Python 3.8+ installed on your machine.
 ### Installation
 1. Clone this repository:
    ```bash
-   git clone https://github.com/mhdsahil1/CodeAlpha_SecureCodingReview.git
+   git clone https://github.com/rohans37/CodeAlpha_SecureCodingReview.git
    cd CodeAlpha_SecureCodingReview
    ```
```

## TODO / FIXME / HACK Notes

No TODO/FIXME/HACK notes found in selected files.

## Selected File Context

### README.md

| Field | Value |
| --- | --- |
| Bytes | 4870 |
| Score | 225 |
| Why | changed, project-metadata, high-signal-doc |
| Status | Full content |


```markdown
# 🛡️ Secure Coding Review (CodeAlpha)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Flask](https://img.shields.io/badge/Flask-3.0.3-green)
![Bandit](https://img.shields.io/badge/Bandit-SAST-orange)
![Security](https://img.shields.io/badge/Security-Code%20Review-red)

A comprehensive Secure Coding Review project developed for **CodeAlpha**. This repository demonstrates common web application vulnerabilities and their corresponding secure implementations using Python and Flask. It includes a vulnerable application, a remediated secure application, and an in-depth security audit report.

## 📑 Table of Contents
- [Project Overview](#-project-overview)
- [Vulnerabilities Explored](#-vulnerabilities-explored)
- [Repository Structure](#-repository-structure)
- [Tools Used](#-tools-used)
- [Getting Started](#-getting-started)
- [Usage](#-usage)
- [Disclaimer](#-disclaimer)

## 🎯 Project Overview
The goal of this project is to perform a manual and automated code review to identify security flaws in a web application and provide actionable remediation steps. 
Two versions of a Flask application are provided:
1. **`vulnerable_app.py`**: Intentionally includes critical security flaws.
2. **`secure_app.py`**: The patched version adhering to secure coding best practices.

A detailed **[Code Review Report](Code_Review_Report.md)** is included, detailing findings, risks, and fixes.

## 🐛 Vulnerabilities Explored
This project covers the following critical vulnerabilities (inspired by the OWASP Top 10):
1. **Hardcoded Secrets (Sensitive Data Exposure)**
2. **SQL Injection (SQLi)**
3. **Cross-Site Scripting (Reflected XSS)**
4. **Command Injection**
5. **Plaintext Passwords (Weak Cryptography)**
6. **Missing Authentication (Broken Access Control)**

## 📸 Screenshots & Demonstrations

### 🟥 Vulnerable Dashboard
![Vulnerable Dashboard](Screenshots/home_vulnerable.png)

### 🟩 Secure Dashboard
![Secure Dashboard](Screenshots/home_secure.png)

### 🐛 Vulnerability Demonstrations

**1. SQL Injection (SQLi)**
![SQL Injection](Screenshots/sql_injection.png)

**2. SQL Injection Fixed (Parameterized Queries)**
![SQL Fixed](Screenshots/sql_fixed.png)

**3. Cross-Site Scripting (XSS)**
![XSS Demo](Screenshots/xss_demo.png)

**4. Command Injection**
![Command Injection](Screenshots/ping_demo.png)

**5. Missing Authentication Fixed**
![Admin Protected](Screenshots/admin_protected.png)

### 🛡️ Static Analysis (Bandit)
![Bandit Report](Screenshots/bandit_report.png)

## 📂 Repository Structure
```text
📦 CodeAlpha_Secure_Coding_Review
 ┣ 📜 vulnerable_app.py      # The intentionally vulnerable Flask application
 ┣ 📜 secure_app.py          # The remediated, secure Flask application
 ┣ 📜 Code_Review_Report.md  # Detailed security audit report and remediation steps
 ┣ 📜 bandit_report.txt      # Static Application Security Testing (SAST) results
 ┣ 📜 requirements.txt       # Python dependencies
 ┗ 📜 README.md              # Project documentation
```

## 🛠️ Tools Used
- **Language:** Python 3
- **Web Framework:** Flask, Werkzeug
- **Database:** SQLite3
- **Static Analysis (SAST):** Bandit (Python security linter)

## 🚀 Getting Started

### Prerequisites
Ensure you have Python 3.8+ installed on your machine.

### Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/rohans37/CodeAlpha_SecureCodingReview.git
   cd CodeAlpha_SecureCodingReview
   ```

2. (Optional but recommended) Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## 💻 Usage

### Running the Vulnerable App
```bash
python vulnerable_app.py
```
*The app will run on `http://127.0.0.1:5000`. You can test SQL injection on `/login`, command injection on `/ping`, and bypass authentication on `/admin`.*

### Running the Secure App
```bash
# Set a secure environment variable for the secret key (optional)
export SECRET_KEY="[REDACTED:SECRET]" # On Windows use: set SECRET_KEY="[REDACTED:SECRET]"

python secure_app.py
```
*The secure app mitigates the vulnerabilities. Passwords are hashed using PBKDF2, inputs are sanitized and parameterized, and unauthorized access is blocked.*

### Running Static Analysis (Bandit)
To run the Bandit SAST tool against the vulnerable code yourself:
```bash
pip install bandit
bandit -r vulnerable_app.py
```

## ⚠️ Disclaimer
**Educational Purposes Only:** The `vulnerable_app.py` script contains intentional, critical security vulnerabilities. Do NOT deploy or run the vulnerable application in a production environment or on a public-facing server. This repository is intended strictly for educational purposes and security research.
```

### requirements.txt

| Field | Value |
| --- | --- |
| Bytes | 31 |
| Score | 70 |
| Why | project-metadata |
| Status | Full content |


```txt
Flask==3.0.3
MarkupSafe==2.1.5
```

### bandit_report.txt

| Field | Value |
| --- | --- |
| Bytes | 5214 |
| Score | 0 |
| Why | context |
| Status | Full content |


```txt
Run started:2026-08-07 10:46:58.343397+00:00

Test results:
>> Issue: [B105:hardcoded_password_string] Possible hardcoded password: '[REDACTED:SECRET]'
   Severity: Low   Confidence: Medium
   CWE: CWE-259 (https://cwe.mitre.org/data/definitions/259.html)
   More Info: https://bandit.readthedocs.io/en/1.9.4/plugins/b105_hardcoded_password_string.html
   Location: .\vulnerable_app.py:9:17
8	# Hardcoded Secret (Vulnerability 1: Sensitive Data Exposure)
9	SECRET_API_KEY = "[REDACTED:SECRET]"
10	

--------------------------------------------------
>> Issue: [B608:hardcoded_sql_expressions] Possible SQL injection vector through string-based query construction.
   Severity: Medium   Confidence: Low
   CWE: CWE-89 (https://cwe.mitre.org/data/definitions/89.html)
   More Info: https://bandit.readthedocs.io/en/1.9.4/plugins/b608_hardcoded_sql_expressions.html
   Location: .\vulnerable_app.py:33:18
32	        # Vulnerable SQL query using string formatting
33	        query = f"SELECT * FROM users WHERE username = '{username}' AND password = '[REDACTED:SECRET]}'"
34	        cursor.execute(query)

--------------------------------------------------
>> Issue: [B605:start_process_with_a_shell] Starting a process with a shell, possible injection detected, security issue.
   Severity: High   Confidence: High
   CWE: CWE-78 (https://cwe.mitre.org/data/definitions/78.html)
   More Info: https://bandit.readthedocs.io/en/1.9.4/plugins/b605_start_process_with_a_shell.html
   Location: .\vulnerable_app.py:63:15
62	    # Vulnerable to Command Injection
63	    response = os.popen(f"ping -c 1 {ip}").read()
64	    return f"<pre>{response}</pre>"

--------------------------------------------------
>> Issue: [B201:flask_debug_true] A Flask app appears to be run with debug=True, which exposes the Werkzeug debugger and allows the execution of arbitrary code.
   Severity: High   Confidence: Medium
   CWE: CWE-94 (https://cwe.mitre.org/data/definitions/94.html)
   More Info: https://bandit.readthedocs.io/en/1.9.4/plugins/b201_flask_debug_true.html
   Location: .\vulnerable_app.py:74:4
73	    init_db()
74	    app.run(debug=True)

--------------------------------------------------

Code scanned:
	Total lines of code: 52
	Total lines skipped (#nosec): 0
	Total potential issues skipped due to specifically being disabled (e.g., #nosec BXXX): 0

Run metrics:
	Total issues (by severity):
		Undefined: 0
		Low: 1
		Medium: 1
		High: 2
	Total issues (by confidence):
		Undefined: 0
		Low: 1
		Medium: 2
		High: 1
Files skipped (0):
```

### Code_Review_Report.md

| Field | Value |
| --- | --- |
| Bytes | 8353 |
| Score | 0 |
| Why | context |
| Status | Full content |


```markdown
# Secure Coding Review Report

## 1. Overview
- **Application Audited:** Python Flask Web Application (`vulnerable_app.py`)
- **Review Type:** Manual Code Inspection
- **Objective:** Identify security vulnerabilities, provide recommendations, and suggest remediation steps for safer code.

## 2. Identified Vulnerabilities

### Vulnerability 1: Hardcoded Sensitive Data (Secrets)
- **Location:** `vulnerable_app.py` (Line 8)
- **Description:** The `SECRET_API_KEY` is hardcoded directly into the source code.
- **Risk:** High. Anyone with access to the source code (including version control systems like Git) can read the secret, leading to potential unauthorized access to connected services.
- **Remediation:** Remove hardcoded secrets. Use environment variables or a secure secret management service (e.g., AWS Secrets Manager, HashiCorp Vault) to load sensitive configuration at runtime.
- **Code Fix:**
  ```python
  # Instead of hardcoding:
  # SECRET_API_KEY = "[REDACTED:SECRET]"
  
  # Use environment variables:
  app.secret_key = os.environ.get("SECRET_KEY", "default-dev-key")
  ```

### Vulnerability 2: SQL Injection (SQLi)
- **Location:** `vulnerable_app.py` (Line 31)
- **Description:** User input (`username` and `password`) from the login form is concatenated directly into the SQL query string using f-strings.
- **Risk:** Critical. An attacker can manipulate the input to alter the SQL statement. For example, entering `admin' --` as the username could allow authentication without a password, or worse, allow arbitrary database extraction or deletion.
- **Remediation:** Always use parameterized queries (prepared statements). This ensures the database treats the inputs as data, not executable code.
- **Code Fix:**
  ```python
  # Vulnerable:
  # query = f"SELECT * FROM users WHERE username = '{username}' AND password = '[REDACTED:SECRET]}'"
  # cursor.execute(query)

  # Secure (Parameterized Query):
  query = "SELECT * FROM users WHERE username = ? AND password = ?"
  cursor.execute(query, (username, password))
  ```

### Vulnerability 3: Cross-Site Scripting (Reflected XSS)
- **Location:** `vulnerable_app.py` (Line 46-49)
- **Description:** The application takes the `name` parameter from the URL and reflects it directly into the HTML response without any sanitization or escaping.
- **Risk:** High. An attacker can craft a malicious URL (e.g., `?name=<script>alert(1)</script>`). When a victim clicks the link, the malicious script executes in their browser, potentially stealing session cookies or performing actions on their behalf.
- **Remediation:** Always sanitize or escape user-supplied data before rendering it in HTML. Modern templating engines like Jinja2 (used by Flask) perform context-aware auto-escaping when variables are passed correctly.
- **Code Fix:**
  ```python
  # Vulnerable:
  # template = f"<h1>Hello, {name}!</h1>"
  # return render_template_string(template)

  # Secure (Using Jinja2 variables for auto-escaping):
  template = "<h1>Hello, {{ name }}!</h1>"
  return render_template_string(template, name=name)
  ```

### Vulnerability 4: Command Injection
- **Location:** `vulnerable_app.py` (Line 54-58)
- **Description:** The application takes an IP address from the user and concatenates it directly into a system command executed via `os.popen()`.
- **Risk:** Critical. An attacker can append arbitrary system commands. For example, passing `127.0.0.1; cat /etc/passwd` allows the attacker to read arbitrary files from the server or gain a reverse shell.
- **Remediation:** Avoid invoking system shells. If executing system commands is necessary, use APIs that do not invoke a shell (like `subprocess.run` with a list of arguments) and strictly validate user input (e.g., using regex to ensure the input is a valid IP address).
- **Code Fix:**
  ```python
  # Vulnerable:
  # response = os.popen(f"ping -c 1 {ip}").read()

  # Secure (Input Validation + Safe Execution):
  import re, subprocess
  
  if not re.match(r"^\d{1,3}(\.\d{1,3}){3}$", ip):
      return "Invalid IP address format.", 400

  result = subprocess.run(['ping', '-c', '1', ip], capture_output=True, text=True, timeout=5)
  response = result.stdout
  ```

### Vulnerability 5: Plaintext Passwords
- **Location:** `vulnerable_app.py` (Database initialization and schema)
- **Description:** Passwords are stored in the database in plaintext (`password TEXT`, and `admin123`).
- **Risk:** Critical. If the database is compromised, attackers gain immediate access to all user accounts.
- **Remediation:** Hash passwords using strong algorithms like PBKDF2 (provided by Werkzeug) before storing them. Validate passwords by comparing hashes instead of plaintext strings.
- **Code Fix:**
  ```python
  # Vulnerable:
  # cursor.execute('''INSERT INTO users (id, username, password) VALUES (1, 'admin', 'admin123')''')
  
  # Secure:
  from werkzeug.security import generate_password_hash, check_password_hash
  hashed_pw = generate_password_hash('admin123')
  cursor.execute('''INSERT INTO users (id, username, password) VALUES (1, 'admin', ?)''', (hashed_pw,))
  ```

### Vulnerability 6: Missing Authentication (Broken Access Control)
- **Location:** `vulnerable_app.py` (Line 67)
- **Description:** The `/admin` route is publicly accessible without any authentication or authorization checks.
- **Risk:** High. Attackers can access administrative features directly by navigating to the URL, bypassing the intended login mechanism.
- **Remediation:** Implement session management and enforce authentication checks on sensitive routes.
- **Code Fix:**
  ```python
  # Vulnerable:
  # @app.route('/admin')
  # def admin():
  #     return "<h1>Admin Dashboard</h1>"
  
  # Secure:
  @app.route('/admin')
  def admin():
      if not session.get('logged_in'):
          return "Unauthorized", 401
      return "<h1>Admin Dashboard</h1>"
  ```

## 3. Best Practices & Recommendations
1. **Never Trust User Input:** Validate, sanitize, and encode all input received from untrusted sources (users, external APIs, etc.). Implement strict allowlisting for validation where possible.
2. **Use Security Linters (Static Analysis):** Integrate SAST tools like **Bandit** for Python into the CI/CD pipeline. 

> [!NOTE]
> **Static Analysis Screenshot (Bandit Output)**
> Static analysis was performed using Bandit on the vulnerable application, successfully identifying the hardcoded secrets, SQL injection, and command injection risks:
> 
> ```text
> [main]	INFO	running on Python 3.13.14
> Run started:2026-08-07 10:47:16
> 
> Test results:
> >> Issue: [B105:hardcoded_password_string] Possible hardcoded password: '[REDACTED:SECRET]'
>    Severity: Low   Confidence: Medium
>    Location: .\vulnerable_app.py:9:17
> 
> >> Issue: [B608:hardcoded_sql_expressions] Possible SQL injection vector through string-based query construction.
>    Severity: Medium   Confidence: Low
>    Location: .\vulnerable_app.py:33:18
> 
> >> Issue: [B605:start_process_with_a_shell] Starting a process with a shell, possible injection detected, security issue.
>    Severity: High   Confidence: High
>    Location: .\vulnerable_app.py:63:15
> 
> >> Issue: [B201:flask_debug_true] A Flask app appears to be run with debug=True...
>    Severity: High   Confidence: Medium
>    Location: .\vulnerable_app.py:74:4
> 
> Run metrics:
> 	Total issues (by severity):
> 		Low: 1
> 		Medium: 1
> 		High: 2
> ```
3. **Principle of Least Privilege:** Run the application with a dedicated user account with only the permissions necessary to function. The database user should only have access to the specific tables needed.
4. **Dependency Management:** Regularly scan dependencies for known vulnerabilities using tools like `pip-audit` or Dependabot.
5. **Disable Debug Mode in Production:** Ensure `app.run(debug=False)` or run the application through a production WSGI server (like Gunicorn) in deployment, as debug mode can expose interactive debuggers and sensitive stack traces to attackers.

## 4. Conclusion
The initial version of the application contained critical vulnerabilities that could lead to full system compromise and data breaches. By applying parameterized queries, proper output encoding, input validation, and secure system call methods, the risks have been mitigated. The updated `secure_app.py` reflects these remediation steps.
```

### secure_app.py

| Field | Value |
| --- | --- |
| Bytes | 18891 |
| Score | -1 |
| Why | context |
| Status | Truncated (budget limit) |

**Structural Outline:**
  - `def init_db` (line 16)
  - `def index` (line 28)
  - `def login` (line 68)
  - `def greet` (line 161)
  - `def ping` (line 198)
  - `fn match` (line 202)
  - `def admin` (line 305)


```py
// … lines 1–21
from flask import Flask, request, render_template_string, session, redirect, url_for
from werkzeug.security import generate_password_hash, check_password_hash
from markupsafe import escape
import sqlite3
import os
import subprocess
import re
import platform

app = Flask(__name__)

# FIX 1: Secrets should be loaded from environment variables, never hardcoded.
# Example: export SECRET_KEY="[REDACTED:SECRET]"
app.secret_key = os.environ.get("SECRET_KEY", "default-dev-key")

def init_db():
    conn = sqlite3.connect('users.db')
    cursor = conn.cursor()
    cursor.execute('''DROP TABLE IF EXISTS users''') # Drop to ensure fresh schema with hashed passwords
    cursor.execute('''CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, username TEXT, password TEXT)''')
    # FIX 5: Hash passwords using PBKDF2 (Werkzeug default)
// … lines 27–32
@app.route('/')
def index():
    return '''
    <!DOCTYPE html>
    <html lang="en">
    <head>
// … lines 67–72
@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        
// … lines 160–165
@app.route('/greet')
def greet():
    name = request.args.get('name', 'Guest')
    # Secure against XSS: Using Jinja2 context variables ensures auto-escaping
    template = '''
    <!DOCTYPE html>
// … lines 197–206
@app.route('/ping')
def ping():
    ip = request.args.get('ip', '127.0.0.1')
    
    # Input validation: Ensure the input looks like an IP address
    if not re.match(r"^\d{1,3}(\.\d{1,3}){3}$", ip):
        return '''
        <!DOCTYPE html>
        <html lang="en">
        <head>
// … lines 304–309
@app.route('/admin')
def admin():
    if not session.get('logged_in'):
        return '''
        <!DOCTYPE html>
        <html lang="en">
```

### vulnerable_app.py

| Field | Value |
| --- | --- |
| Bytes | 14787 |
| Score | -1 |
| Why | context |
| Status | Truncated (budget limit) |

**Structural Outline:**
  - `def init_db` (line 12)
  - `def index` (line 21)
  - `def login` (line 61)
  - `def greet` (line 179)
  - `def ping` (line 216)
  - `def admin` (line 258)


```py
// … lines 1–5
# pyrefly: ignore [missing-import]
from flask import Flask, request, render_template_string
import sqlite3
import os
import platform
// … lines 11–16

def init_db():
    conn = sqlite3.connect('users.db')
    cursor = conn.cursor()
    cursor.execute('''CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, username TEXT, password TEXT)''')
    cursor.execute('''INSERT OR IGNORE INTO users (id, username, password) VALUES (1, 'admin', 'admin123')''')
// … lines 20–25
@app.route('/')
def index():
    return '''
    <!DOCTYPE html>
    <html lang="en">
    <head>
// … lines 60–65
@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        
// … lines 178–183
@app.route('/greet')
def greet():
    name = request.args.get('name', 'Guest')
    # Vulnerable to Reflected XSS
    template = f'''
    <!DOCTYPE html>
// … lines 215–220
@app.route('/ping')
def ping():
    ip = request.args.get('ip', '127.0.0.1')
    # Vulnerable to Command Injection
    count_flag = "-n" if platform.system() == "Windows" else "-c"
    response = os.popen(f"ping {count_flag} 1 {ip}").read()
// … lines 257–262
@app.route('/admin')
def admin():
    # Anyone can access this page without logging in!
    return '''
    <!DOCTYPE html>
    <html lang="en">
```