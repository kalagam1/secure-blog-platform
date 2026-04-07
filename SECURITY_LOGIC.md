# 🛡️ Security Implementation Snippets

This document highlights the core "Defense in Depth" logic implemented in this project to mitigate OWASP Top 10 vulnerabilities.

## 1. SQL Injection Prevention (Prepared Statements)
Instead of concatenating user input into SQL strings, I used **PDO Prepared Statements**. This ensures that user input is treated as data only, never as executable code.

```php
// Example: Securely fetching a post by ID
$stmt = $pdo->prepare('SELECT * FROM posts WHERE id = :id');
$stmt->execute(['id' => $_GET['id']]);
$post = $stmt->fetch();
```

## 2. CSRF Protection (Token Validation)
To prevent Cross-Site Request Forgery, I implemented a per-session token system. Every state-changing request (like deleting a post) must include a valid token that matches the one stored in the user's session.

```php
// Step 1: Generate and store token in session
$_SESSION['csrf_token'] = bin2hex(random_bytes(32));

// Step 2: Validate token on the processing page (e.g., delete_post.php)
if (!isset($_POST['csrf_token']) || $_POST['csrf_token'] !== $_SESSION['csrf_token']) {
    die("CSRF token validation failed.");
}
// Proceed with deletion only if token is valid
```

## 3. XSS Mitigation (Output Encoding)
To prevent Stored and Reflected XSS, all user-generated content is sanitized before being rendered in the browser.

```php
// Encoding output to neutralize malicious scripts
echo htmlspecialchars($post['body'], ENT_QUOTES, 'UTF-8');
```

## 4. Secure Credential Storage (Bcrypt)
Passwords are never stored in plain text. I utilized PHP’s password_hash with the PASSWORD_DEFAULT (Bcrypt) algorithm.

```php
// Hashing during registration
$hashedPassword = password_hash($userPassword, PASSWORD_DEFAULT);

// Verifying during login
if (password_verify($inputPassword, $storedHash)) {
    // Login success
}
```
