# SecureCoding-CodeAlpha
ask 3: Secure Coding Review (Security Audit)OverviewPerformed a Static Application Security Testing (SAST) audit on a Python application to identify common security vulnerabilities. The audit was conducted using Bandit, a tool designed to find common security issues in Python code.Audit ResultsThe scan identified 3 key vulnerabilities in the initial source code:SeverityVulnerability TypeDescriptionHighSQL InjectionUsing string formatting (%s) to build SQL queries from user input.MediumHardcoded SecretSensitive administrative credentials stored directly in the source code.LowShell InjectionUsing os.system() which can allow execution of arbitrary shell commands.
Remediation (How I Fixed It)
1. Preventing SQL Injection
The Problem: The application was "gluing" user input directly into the SQL string.

The Fix: Implemented Parameterized Queries using ? placeholders. This ensures the database treats input as data only, never as executable code.

2. Securing Sensitive Data
The Problem: The admin password was visible to anyone with access to the code.

The Fix: Removed hardcoded strings. In a production environment, these would be managed via Environment Variables or a Secret Manager.

3. Secure Process Execution
The Problem: os.system is easily manipulated by attackers.

The Fix: Recommended the use of the subprocess module with shell=False for safer system interactions.
