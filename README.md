# 🔐 Secure-Blog: Multi-User Platform with Defense-in-Depth

## 📌 Project Overview
This is a full-stack blogging application engineered with a **Security-First** mindset. It demonstrates the implementation of professional-grade security controls to mitigate the OWASP Top 10 vulnerabilities.

![Dashboard Preview](screenshots/dashboard_preview.png)

## 🛡️ Security Features
* **SQL Injection Protection:** Utilizes **PDO Prepared Statements** for all database interactions.
* **CSRF Protection:** (Shown in screenshot) Implemented unique per-session tokens for sensitive actions like **Post Deletion**.
* **Role-Based Access Control (RBAC):** (Shown in screenshot) Logic to differentiate between `User` and `Superuser` permissions.
* **XSS Defense:** Strict input sanitization using `htmlspecialchars()`.
* **Secure Authentication:** Password storage using `password_hash()` (Bcrypt).

## 🛠️ Tech Stack
* **Backend:** PHP, MySQL
* **Frontend:** HTML5, CSS3, JavaScript
* **Tools:** XAMPP, VS Code

## 📸 Security & UI Gallery

| **Role-Based Access (Admin)** | **CSRF Verification** |
|:---:|:---:|
| ![Admin Dashboard](screenshots/01_admin_dashboard.png) | ![CSRF Check](screenshots/02_csrf_protection.png) |

| **Secure Hashed Credentials** | **Real-Time Concurrent Chat** |
|:---:|:---:|
| ![Database](screenshots/03_database_security.png) | ![Chat System](screenshots/04_realtime_chat.png) |

## 📂 Folder Structure
* `/src`: Application logic and security middleware.
* `/database`: SQL schema and relational design.
* `/screenshots`: UI previews and security verification.

## 🛠️ Installation & Setup
1. Clone the repository.
2. Import `database/schema.sql` into your MySQL server.
3. Configure `db_connect.php` with your local credentials.
4. Run via XAMPP/Apache on `localhost`.

## 📺 Video Demo
[Link to your YouTube Demo](https://youtu.be/vQwIPN550TQ?feature=shared)

---
*Developed as part of the Secure Application Development (SECAD) curriculum at the University of Dayton.*
