# 🐾 TriVet: Enterprise-Grade Offline-First Veterinary ERP & Autonomous CRM

**[ 🔗 Watch the Clinic Director's Endorsement ](https://youtube.com/shorts/YXOO-PCw0xQ?feature=share)**

---
## 📌 Executive Summary

**TriVet** is a proprietary, offline-first Enterprise Resource Planning (ERP) and Shop Management System engineered specifically for high-volume veterinary hospitals operating in regions with unstable internet infrastructure. 

It is not a standard web application. It is a **compiled, hardware-bound, on-premise SaaS appliance** that turns a single clinic PC into an unbreachable LAN server, reachable from any tablet, phone, or workstation via ZeroConf.

The system digitizes clinical workflows end-to-end, manages **batch-level inventory with FIFO cost accounting**, and drives recurring revenue through an **autonomous multilingual WhatsApp CRM engine**. 

To enforce a strict B2B subscription model without relying on cloud licensing servers, the entire Python/Flask backend is compiled to native C via **Nuitka** and fortified with a military-grade Asymmetric Cryptographic DRM engine.

---

## 📈 Live Market Data (15-Month Pilot Study)

Before commercial release, TriVet operated silently in a high-volume clinic in **Sulaymaniyah, Iraq** to gather unbiased performance data and validate the architecture:

*   **Processed 5,616 paying transactions flawlessly** using the offline-first, dual-currency POS.
*   **Tracked 6,309,520 IQD in Revenue Leakage** — the system autonomously identified 280 "No-Show" appointments, giving clinic ownership complete visibility into evaporated revenue and mitigating future losses via the WhatsApp CRM.
*   **Eliminated "Room Service" Shrinkage** — successfully deployed the **Financial Interceptor**, autonomously capturing unbilled medical procedures performed on boarded pets and routing them to the correct checkout folio.

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

### 🤖 Autonomous CRM Engine
Seven background daemons dispatch localized WhatsApp/Email recalls, appointment reminders, overdue boarding nags, and abandoned-cart alerts. Includes a strict Twilio messaging-policy validator to prevent account suspension.

### ⚡ 100% Operational Uptime
Deployed strictly on local clinic hardware. Immune to regional ISP outages. Utilizes mDNS to broadcast the app seamlessly to internal iPads. The host PC holds a Windows Sleep-Block to ensure the server never naps.

### 🔒 Zero-Leakage Financials
Dual-currency POS with historical COGS tracking, shift-based cash reconciliation, per-channel attribution, and an Admin-PIN gate for high-discount sales.

### 🏥 Hotel Revenue Capture
Multi-cage bookings with rate segments preventing retroactive repricing. Mid-stay deposits auto-credit to a unified customer balance, which auto-pays outstanding debts first.

### 📊 Customer Intelligence
Automated VIP loyalty tiers (VIP/Gold/Silver/Bronze), churn predictions (Champion/Active/At-Risk/Lost), next-visit forecasting, day/hour purchase heatmaps, and birthday radar.

### 📦 Inventory Reconciliation
Session-based physical counts with "Blind Mode" (hides expected quantities to prevent counter bias), extendable reason picklists, and one-shot variance application to underlying FIFO batches.

---

## 🛡️ Defense-in-Depth Security & Anti-Reversing Engine

> ⚠️ **PROPRIETARY BLACK-BOX ARCHITECTURE**
> 
> TriVet binaries are compiled directly to native C. The source code is strictly proprietary, and decompilation is aggressively mitigated. Any attempt to extract, reverse-engineer, or feed the binaries to an automated decompiler for resale will result in an incomplete, non-functional build completely stripped of its cryptographic bindings.

To protect intellectual property in an offline environment, TriVet employs an impenetrable, multi-layered defense grid:

*   **Hardware-Anchored DRM:** Software cannot be copied to a new machine. Licenses are mathematically bound to a composite silicon fingerprint (Motherboard UUID + Volume Serial).
*   **Asymmetric Cryptographic Signatures:** All license keys and override tokens are verified using Ed25519 (Curve25519) Asymmetric Cryptography. The private key never exists on the client machine; it is mathematically impossible to forge a valid license without vendor intervention.
*   **Temporal Lockout Sentinels:** The system actively monitors the OS clock against external NTP anchors and internal monotonic timestamps. Winding the clock backward to extend a license instantly triggers a cryptographic lockdown requiring a vendor-signed payload to unlock.
*   **Memory-Resident Execution:** The application does not extract HTML, CSS, or SQL files to the disk. All UI assets are packed into Base64 strings and executed directly from RAM via a custom Jinja2 loader, preventing local tampering or scraping.
*   **Active Anti-Tamper & Anti-Debug:** The compiled binary features silent execution guards. It actively probes for blacklisted reverse-engineering tools (x64dbg, IDA Pro, Ghidra, Process Hacker), debuggers, and virtualization environments via Win32 API calls. If tampering is detected, the application silently terminates before memory can be dumped.
*   **Military-Grade Secret Management:** Local database credentials, API keys, and Fernet encryption peppers are wrapped by OS-level DPAPI, bound cryptographically to the Windows user and physical machine ID.

---

## 🛠️ Tech Stack & Architecture

*   **Backend / API:** Python 3, Flask, Waitress WSGI (40 threads, 200 connection limit), APScheduler.
*   **Database Engine:** PostgreSQL 16+ — **Thick PL/pgSQL architecture** heavily utilizing triggers, `FOR UPDATE` row locks, and `pg_advisory_xact_lock` for thread-safe sequence generation.
*   **Connection Pool:** `psycopg2` Threaded Connection Pool (min=1, max=50) with active pool-poisoning detection and auto-recovery.
*   **Frontend:** Server-rendered Jinja2, Vanilla JS, SweetAlert2, Chart.js, FontAwesome, Flatpickr. Fully RTL-aware.
*   **External APIs:** Twilio (WhatsApp/SMS), SMTP, TriTakion Cloudflare Worker (Cloud Catalogue Mirror & Boss Dashboard Feed).

---

## ⚙️ Core Engineering Achievements

### 🗄️ "Thick DB" Architecture & Idempotent Migrations
The PostgreSQL schema is engineered to handle heavy business logic, keeping the Python API exceptionally fast and transactional.

*   **Autonomous Bootstrapping:** A custom, sequential migration engine (V1 to V55) autonomously connects to Postgres, builds the database, injects 50+ relational tables, and builds `PL/pgSQL` triggers. A boot-time integrity guard refuses to start the server if the code and schema ever diverge.
*   **Database-Level State Management:** The Python layer only mutates underlying ledger tables. Triggers automatically maintain cached columns (e.g., `inventory.quantity` automatically recalculates from active batches; `customers.account_balance` auto-syncs from the credit ledger).
*   **Immutable Forensic Audit:** A PostgreSQL `RULE` physically prevents any `DELETE` from the audit logs. Every void, adjustment, and clinical edit is permanently stamped with JSONB snapshots of the old and new data.
*   **Smart Soft-Deletes:** Partial unique indexes allow for the "soft-deletion" of customer records while automatically freeing up unique constraints (Emails/Phones) for future use, preventing database collisions.

### 💵 Forensic Accounting & Dual-Currency POS
Engineered specifically for the Middle Eastern market, where purchases are USD-denominated but billing is IQD.

*   **Batch-Level FIFO Costing:** `inventory_batches` is the absolute source of truth. Every consumed unit is traced to a specific batch, cost, and receipt line via append-only forensic logs.
*   **DB-Backed Idempotency:** Checkouts are claimed in a `processed_transactions` table inside the same transaction. A client retry after a crash **cannot** double-charge, as the claim rolls back cleanly with the sale.
*   **250-IQD Rounding to the Books:** The POS rounds to the nearest 250 IQD. The resulting surcharge lands in a generated database column (`rounding_adjustment`), ensuring the balance identity holds exactly across the general ledger.

### 🏥 Hotel & Inpatient Subsystem (The Financial Interceptor)
*   **Rate Segments:** Mid-stay cage transfers create new rate segments. Past nights never retroactively reprice.
*   **Multi-Cage Bookings:** Supports litters across multiple cages. The check-in modal dynamically excludes already-selected cages.
*   **Owner Live Feed:** An unguessable, LAN-only live feed allowing pet owners to track their boarding pets via QR code, protected by per-boarding kill switches.
*   **Recurring Care Plans:** APScheduler heartbeats automatically generate 48-hour rolling task horizons for DAILY, INTERVAL, and ONCE medical care plans.

### 🤖 Autonomous CRM & Clinical Automation
*   **Background Daemons:** Includes automated appointment reminders, vaccine recalls (with a 3-day catch-up window), nightly backups, and Twilio monthly quota alerts.
*   **Message Template Editor:** Clinics author custom WhatsApp/Email bodies. A strict validator enforces Twilio's Messaging Policy (variable caps, prohibited-terms blocklist) server-side to prevent account suspension.
*   **Directional Isolates (FSI/PDI):** Substituted Latin-script values (like an English owner name) are wrapped in Unicode isolates so Arabic and Kurdish messages do not visually invert on the customer's phone.

### 📦 Physical Inventory Count (Blind Mode)
*   **Bias-Free Counting:** A "Blind Mode" hides expected quantities from non-admin counters until they enter their count.
*   **One-Shot Variance Application:** Completing a session generates `manual_adjustment` movements on the underlying batches, never on the cached column. Quantities reconcile against current stock so the invariant `new_qty = old_qty + delta` holds strictly.
*   **Print-Ready Worksheets:** Generates blank hand-count worksheets and final audit copies, fully translated and RTL-aware.

### 🌩️ Automated Disaster Recovery & Data Sovereignty
*   **AES-Encrypted Backups:** Nightly `pg_dump -Fc` encrypted via Fernet, using a key derived from the machine ID + a recovery salt. The plaintext dump is deleted inside a `finally` block to prevent data leaks.
*   **Cryptographic "Time Machine":** A 1-click database rollback in the Admin Dashboard requires a single-use, 15-minute-expiring Vendor Override Key (Ed25519-verified) to execute.
*   **Data Sovereignty Export:** Produces a ZIP of every table as CSV, with a UTF-8 BOM so Excel opens Kurdish/Arabic script natively. Deliberately reachable from the Trial-Ended screen.

### 🌍 Full RTL & Multilingual UI
*   Every surface (EN / AR / KU) carries dictionary entries and direction-aware CSS.
*   **Font Switching:** Poppins (EN) / Cairo-Tajawal (AR) / Vazirmatn (KU) loaded via a `--global-font` CSS variable.
*   **Dark Mode & Font Adjuster:** Persisted to `localStorage`, applied before first paint to avoid a flash of unstyled content.

---

## 🗺️ System Architecture Topology

```mermaid
graph TD
    subgraph Local Clinic Network
        A[iPads / Terminals / Phones] -->|mDNS ZeroConf .local| B(Waitress WSGI Server, 40 threads)
        F[Host Hardware Fingerprint] -->|Ed25519 Signature Verify| G{Cryptographic DRM Engine}
        G -.->|Validates Tier| B
        G <-->|DPAPI-wrapped Fernet Pepper| T[tri_secrets.py]
        B <-->|ThreadedConnectionPool 1-50| C[(PostgreSQL 16+)]
        C -.->|PL/pgSQL Triggers maintain cached columns| C
        C -.->|Nightly pg_dump -Fc| D[Background Backup Daemon]
        D -->|Fernet AES-128, machine_id + RECOVERY_SALT| E[(Encrypted AES Backup Store)]
        E -.->|Cross-machine recovery via Recovery ID| G
        B -.->|7 background jobs| K[APScheduler]
    end

    subgraph External Integrations
        K -->|REST API| H[Twilio WhatsApp / SMS]
        K -->|SMTP| I[Email Delivery]
        K -->|POST every 15 min| W[TriTakion Cloudflare Worker]
        W -->|Read-only catalogue| V[Clinic Website / Mobile]
        W -->|Boss Dashboard| X[Owner's Phone]
    end

---

📫 Let's Connect

TriVet represents my ability to take a complex business problem and engineer a secure, scalable, and beautiful full-stack solution from scratch.

    Looking to hire a Senior Backend / Full-Stack Engineer? Let's talk.

    Want to deploy TriVet in your clinic? Reach out for a demo.

Email: AlandDiary@outlook.com



> **© 2026 TriTakion. All Rights Reserved.**  
> *The architectural documentation, system diagrams, and media assets presented in this repository are the intellectual property of the author. They may not be copied, reproduced, or used without express permission.*

