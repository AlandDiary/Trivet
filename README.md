# 🐾 TriVet: Enterprise-Grade Offline-First Veterinary ERP & SMS

**[ 🔗 Watch the Clinic Director's Endorsement ](https://youtube.com/shorts/YXOO-PCw0xQ?feature=share)**

<div align="center">
  <img src="https://img.shields.io/badge/Python_3-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/PostgreSQL_16-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask" />
  <img src="https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E" alt="JavaScript" />
</div>

---

## 📌 Executive Summary

**TriVet** is a proprietary, **offline-first** Enterprise Resource Planning (ERP) and Shop Management System (SMS) engineered specifically for high-volume veterinary hospitals operating in regions with unstable internet infrastructure. It is not a standard web application; it is a **compiled, highly secure on-premise SaaS appliance.**

The system completely digitizes clinical workflows, manages fractional **dual-currency (IQD/USD) inventory**, and actively drives recurring revenue via an autonomous **WhatsApp CRM engine**. To enforce a B2B subscription model without relying on cloud licensing servers, the Python/Flask backend is compiled to native C binaries. It is secured by an advanced Ed25519 asymmetric cryptographic licensing engine featuring hardware-UUID binding and NTP-validated temporal drift protection.

---

## 📈 Live Market Data (15-Month Pilot Study)

Before commercial release, TriVet operated silently in a high-volume clinic in Sulaymaniyah, Iraq to gather unbiased performance data and validate its architecture:

* 💳 **Processed 5,616 paying transactions** flawlessly using the offline-first dual-currency POS.
* 🛑 **Tracked 6,309,520 IQD in Revenue Leakage:** The system autonomously identified 280 "No-Show" appointments, giving clinic ownership complete visibility into evaporated revenue and mitigating future losses via the WhatsApp CRM.
* 📉 **Eliminated "Room Service" Shrinkage:** Successfully deployed the *Financial Interceptor*, autonomously capturing unbilled medical procedures performed on boarded pets and routing them directly to the correct checkout folio.
    
---

## 📸 System Interface & Visual Tour

<div align="center">

  <p><strong>Admin Dashboard View</strong></p>
  <video src="https://github.com/user-attachments/assets/a29d604b-aa72-4c5d-be82-faf599ddcdad" width="800" autoplay loop muted playsinline></video>
  
  <br><br>

  <p><strong>Clinical Medical Visits and Report Generation</strong></p>
  <video src="https://github.com/user-attachments/assets/c60e629f-daa7-40e3-957c-7636e09c7ccc" width="800" autoplay loop muted playsinline></video>
  
  <br><br>

  <p><strong>Checkout POS</strong></p>
  <video src="https://github.com/user-attachments/assets/f01f4eed-327a-4104-90e8-dd8a3034cacb" width="800" autoplay loop muted playsinline></video>

  <br><br>
  
  <p><strong>Inpatient Folio, Hotel Tasks and Services</strong></p>
  <img src="https://github.com/user-attachments/assets/d4ea850c-518a-498a-a625-d4c5555b6339" width="800" alt="TriVet Executive Dashboard">
</div>

---

## 📊 System Impact & Business Value

* 📈 **Autonomous Revenue Generation:** Engineered a background chron engine that automatically dispatches localized *(Arabic / Kurdish / English)* WhatsApp vaccine recalls, directly converting patient data into recurring clinic revenue.
* ⚡ **100% Operational Uptime:** Deployed directly on local hardware. The system is immune to regional ISP outages, utilizing **ZeroConf (mDNS)** multicast routing to broadcast the application to internal clinic iPads and mobile terminals.
* 🔒 **Zero-Leakage Financials:** Processed thousands of transactions with absolute mathematical precision utilizing a dual-currency Point-of-Sale (POS). Features historical Cost of Goods Sold (COGS) tracking and strict shift-based cash drawer management.

---

## 🛠️ Tech Stack & Architecture

* **Backend / API:** `Python 3`, `Flask`, `Waitress WSGI`, `APScheduler`
* **Database Engine:** `PostgreSQL 16` *(Thick DB Architecture with Thread-Safe Pooling)*
* **Frontend:** Server-Side Rendered `Jinja2`, `Vanilla JS`, `CSS3 Variables`, `Chart.js`, `SweetAlert2`
* **Compilation & Security:** `Nuitka` *(C-Compiled Binaries)*, `Ed25519 Asymmetric PEM`, `Fernet (AES-128)`, Windows DPAPI
* **External APIs:** `Twilio` *(WhatsApp/SMS)*, `SMTP` *(Email)*, `Cloudflare Workers` *(Cloud Mirror API)*
* **DevOps & Packaging:** `InnoSetup`, Native Windows APIs (ctypes)

---

## ⚙️ Core Engineering Achievements

### 1. 🛡️ Hardware-Bound Licensing & System Integrity
To enforce a strict SaaS tier model *(PRO, ENTERPRISE)* in an **offline environment**, the software relies on an advanced, hardware-bound integrity engine:
* **Hardware Fingerprinting:** Dynamically extracts a composite hardware UUID, permanently binding the software license to the physical server.
* **Asymmetric Cryptography & RAM-Baking:** Subscription payloads are privately signed via a master `private_key.pem` and verified mathematically by the client. To prevent localized UI tampering, all HTML/JS templates are packed into Base64 strings and **loaded directly into RAM** at runtime.
* **Temporal Validation:** The system queries `pool.ntp.org` to validate the OS clock. If temporal drift or clock-rollback is detected, the system safely suspends access to protect data integrity and subscription validity.

### 2. 🗄️ "Thick DB" Architecture & Idempotent Migrations
The PostgreSQL schema is engineered to handle heavy business logic, keeping the Python API exceptionally fast and transactional:
* **Autonomous Bootstrapping:** A custom, sequential migration engine allows the executable to autonomously connect to Postgres, build the database, inject **30+ relational tables**, and apply strict `PL/pgSQL` triggers and constraints on a fresh install.
* **Smart Soft-Deletes:** Uniquely designed table indexes allow for the "soft-deletion" of customer records while automatically freeing up unique constraints (Emails, Phone Numbers) for future re-use, preventing database collisions.

### 3. 💵 Forensic Accounting, FIFO Inventory & POS
Engineered a financial module designed to operate flawlessly in complex Middle Eastern markets:
* **Dynamic IQD/USD Ledger & FIFO Batches:** The POS tracks inventory in strict **FIFO (First-In, First-Out) batches**. It purchases in USD but dynamically converts to Iraqi Dinar (IQD) based on real-time exchange rates, automatically calculating **exact net-profit margins** per item sold.
* **Anti-Embezzlement Audit Trails:** A robust `JSONB`-powered `audit_logs` table ensures every voided receipt, inventory adjustment, and clinical note edit is permanently stamped.
* **Unified Store Credit:** A unified ledger system for overpayments, hotel deposits, and manual top-ups, allowing cashiers to seamlessly apply customer balances to outstanding debts.

### 4. 🌍 Zero-Reload Multilingual Engine (i18n)
Built a custom, lightweight localization engine directly into the frontend architecture:
* **Dynamic LTR/RTL Switching:** Staff can swap between English (LTR), Arabic (RTL), and Kurdish (RTL) instantly. The DOM dynamically updates text, swaps CSS variables for typography (e.g., *Poppins* to *Cairo*), and mirrors the UI layout **without requiring a server round-trip or page reload**.

### 5. 🤖 Autonomous CRM & Clinical Automation
Transformed the software from a static database into an active business partner:
* **Background Task Scheduler:** Integrated `APScheduler` to run autonomous Python threads in the background without blocking the Waitress WSGI web server.
* **Twilio Integration & Guardrails:** Automatically sweeps the database to dispatch personalized WhatsApp messages. Includes **hard-cap safety limits (Circuit Breakers)** to prevent API billing overages on Twilio's platform.
* **Pet Hotel Care Matrix:** An automated engine that generates recurring daily care tasks (Medication, Feeding) for boarded pets, complete with owner-facing live-feed URLs and automatic Late Checkout fee calculations.

### 6. 🌩️ Disaster Recovery & Data Sovereignty
To mitigate local hardware failure risks (e.g., SSD corruption or Ransomware):
* **AES-Encrypted Backups:** A nightly thread executes a `pg_dump` subprocess, compresses the SQL data, **encrypts it using Fernet (AES-128)** (tied to the specific machine's DPAPI signature), and stores it locally. 
* **Cloud Sync & Developer API:** Pushes authorized inventory snapshots to a Cloudflare Worker via an authenticated background thread, serving as a read-only endpoint for external E-Commerce integrations.
* **Cryptographic "Time Machine":** A 1-click database restoration panel in the Admin Dashboard. Rollbacks require a single-use, **15-minute expiring Vendor Override Key** to execute, protecting daily sales data from unauthorized wipes.

---

## 🗺️ System Architecture Topology

```mermaid
graph TD
    subgraph Local Clinic Network
        A[iPads / Terminals] -->|mDNS ZeroConf| B(Nuitka Compiled Binary / Waitress WSGI)
        F[Hardware UUID & DPAPI] -->|Ed25519 Verification| G{Licensing & Integrity Engine}
        G -.->|Validates Tier| B
        B <-->|Thread-Safe Pool| C[(PostgreSQL 16)]
        C -.->|Nightly ETL| D[Background Scheduler Daemon]
    end
    
    subgraph External Integrations
        D -->|AES-128 Encrypted SQL| E[Local/Cloud Storage]
        B -->|REST API| H[Twilio WhatsApp / SMS]
        B -->|Encrypted Payload| K[Cloudflare Worker Mirror]
        B -->|SMTP| I[Email Delivery]
        G <-->|UDP Ping| J[pool.ntp.org]
    end
