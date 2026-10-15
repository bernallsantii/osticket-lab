## OVERVIEW
This lab covers the end-to-end installation, configuration, and administration of an enterprise-grade ticketing system "osTicket" on Windows Server using IIS, PHP 8.2, and MySQL 8.0. Additionally, it simulates real-world Help Desk operations by configuring Service Level Agreements (SLAs), Departments, Teams, and Help Topics, culminating in full ticket lifecycle triage from intake and identity verification to resolution and escalation.

## ENVIRONMENT & STACK BUILT
* **Operating System:** Windows Server 2022
* **Web Server:** Internet Information Services (IIS) 10.0 + CGI extension + URL Rewrite Module
* **Application Manager:** PHP Manager for IIS + PHP 8.2 (NTS x64)
* **Database Engine:** MySQL Server 8.0 (Database: `osticket`)
* **ITSM Platform:** osTicket v1.17+
* **Core Administration:** Service Level Agreements (Sev-A, Sev-B, Sev-C), Custom Roles, and Help Topics

## PART 1: SYSTEM INSTALLATION & ENVIRONMENT STACK SETUP

### 1. Web Server (IIS) & Extension Configuration
* Enabled Web Server (IIS) with CGI application development roles via Server Manager.
* Installed PHP Manager for IIS and Microsoft URL Rewrite Module.
* Verified web server operation by reaching the default IIS loopback landing page.
<img width="916" height="389" alt="image" src="https://github.com/user-attachments/assets/46b5ce7e-b70d-46ab-8046-e90f447b0bcd" />

### 2. PHP 8.2 Runtime & Extension Registration
* Extracted PHP 8.2 Non-Thread Safe (NTS) files to `C:\PHP`, generated `php.ini`, and registered `php-cgi.exe` within IIS PHP Manager.
* Enabled required extensions (`php_mysqli.dll`, `php_mbstring.dll`, `php_gd.dll`, `php_xml.dll`, `php_intl.dll`, `php_opcache.dll`, `php_imap.dll`)
* <img width="851" height="234" alt="image" src="https://github.com/user-attachments/assets/2df7a62d-a15c-49b5-bab4-dbbd2516aaf2" />

### 3. MySQL Database
* Installed MySQL Server 8.0 running on port 3306 as a Windows Service.
* Verify backend service status in `services.msc`.
<img width="709" height="60" alt="image" src="https://github.com/user-attachments/assets/0c0c503d-87f1-49bc-b6ea-d854d85d3756" />

## PART 2: ITSM SYSTEM CONFIGURATION

### 1. Service Level Agreement (SLA)
* Configured tiered SLA plans to establish strict incident response timeframes and escalation windows:
  * **Sev-A (Critical Outage):** 1-hour grace period, 24/7 coverage.
  * **Sev-B (High Priority):** 4-hour grace period, 24/7 coverage.
  * **Sev-C (Normal Priority):** 8-hour grace period, Business Hours coverage.
  <img width="923" height="426" alt="image" src="https://github.com/user-attachments/assets/eb4395e3-e393-4e9b-9e87-5c00498d081d" />

 ### 2. Help Topics & Automated Ticket Routing Rules
* Created structured end-user entry points mapped directly to specific departments and SLAs to automate ticket routing:
  * **Business Critical Outage:** Routed to `System Administrators` under `Sev-A`.
  * **Personal Computer Issues:** Routed to `Support` under `Sev-C`.
  * **Equipment Request:** Routed to `Support` under `Sev-C`.
  * **Password Reset:** Routed to `Support` under `Sev-B`.
  * **General Inquiries:** Routed to `Support` under `Sev-C`.
  <img width="906" height="872" alt="image" src="https://github.com/user-attachments/assets/5553146c-8b7e-403f-9542-00e5f0d08792" />

## PART 3: TICKET LIFECYCLE TRIAGE & RESOLUTION SIMULATION

### 1. Incident Management & Automated SLA Routing
  * **Critical System Outage (Sev-A):** Processed an emergency ticket for an online banking outage, verifying automatic assignment to **Sev-A** (1-hour response SLA), assigned to the `Online Banking` team, posted operational status updates, and restored system functionality.
  * **Account Access & Identity Verification (Sev-B):** Handled a payroll lockout ticket under **Sev-B** routing, following strict security compliance protocols by verifying user identity prior to delivering temporary credentials securely.
  * **Local Hardware & Software Support (Sev-C):** Resolved an application launch error ticket routed under **Sev-C**, performing software repair and updating local binary files before closing the incident.
<img width="921" height="526" alt="image" src="https://github.com/user-attachments/assets/8b6f6bdc-37ba-42f5-9410-f6f7d796e029" />
<img width="887" height="454" alt="image" src="https://github.com/user-attachments/assets/4b2b50a1-7c74-42f3-ad9e-016a5ba2e0dd" />
<img width="900" height="428" alt="image" src="https://github.com/user-attachments/assets/7152dc91-f6f9-4b89-9707-a3e69bbda89f" />

### 2. Ticket Closure Verification
* Verified that processed tickets met SLA target response times, contained clear internal troubleshooting notes, and were successfully updated to **Resolved / Closed** status.
<img width="923" height="123" alt="image" src="https://github.com/user-attachments/assets/b626e580-d56f-4d60-9476-c93b43cf62ea" />

## KEY COMPETENCIES DEMONSTRATED
**Web & Application Infrastructure:** Web server provisioning (IIS), CGI extension configuration, URL rewriting, and PHP runtime integration.
**Database Administration:** MySQL installation, service management, SQL schema creation, and database user access control.
**Help Desk Security Protocols:** Identity verification compliance prior to account unlocks, least-privilege role assignment, and secure setup directory removal.
