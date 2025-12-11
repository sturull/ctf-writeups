# Web Challenge 01 — Basic Login Bypass

## 📝 Challenge Description
A simple login page was provided.  
The goal was to bypass authentication without knowing a valid username or password.

## 🔍 Step 1: Initial Recon
I tested basic form behavior:
- Tried normal usernames
- Checked for error messages
- Tried invalid passwords

The error message always returned:  
**"Invalid username or password"**

This suggested the page was vulnerable to input manipulation.

## 💡 Step 2: Testing for SQL Injection
I entered this into the username field: admin’ OR ‘1’=’1
And left the password blank.

This is a common test to see if the form sends user input directly into an SQL query.

## 🧪 Step 3: Result
The login succeeded.

This confirmed:
- The site did not sanitize input
- It was vulnerable to classic SQL injection
- User authentication could be bypassed entirely

## 🚩 Flag Obtained
**FLAG: LOGIN_BYPASSED_SUCCESSFULLY**

## 📘 Lessons Learned
- Always test login forms for common injection flaws
- Proper sanitization & parameterized queries are critical
- Even simple challenges teach the importance of secure input handling
