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
  # SECRET_API_KEY = "12345-abcde-super-secret-key"
  
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
  # query = f"SELECT * FROM users WHERE username = '{username}' AND password = '{password}'"
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
> >> Issue: [B105:hardcoded_password_string] Possible hardcoded password: '12345-abcde-super-secret-key'
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
