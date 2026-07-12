# Labeo Receipt Management System (LRMS)

A web-based receipt and payment management system built for **Labeo Montessori** and **Labeo Comprehensive College** — two schools under the Labeo Schools group. LRMS lets bursars look up students, record payments, generate PDF receipts, and produce weekly financial summaries, all backed by Google Sheets instead of a traditional database server.

---

## 1. Overview

| | |
|---|---|
| **Status** | Feature-complete, pending deployment |
| **Type** | Single-file browser application |
| **Backend** | Google Sheets (via Google Sheets API) |
| **Auth** | Google OAuth 2.0 |
| **PDF generation** | jsPDF (client-side) |
| **Hosting target** | Netlify |
| **Schools supported** | Labeo Montessori (primary), Labeo Comprehensive College (secondary) |

### Core Features
- **Login** — Google OAuth sign-in, restricted to authorized bursar accounts
- **Student Lookup** — search by name, class, and section
- **Payment Entry** — record school fees and additional fee categories, via cash or bank transfer
- **Receipt Generation** — auto-numbered, permanent (non-voidable) PDF receipts, downloadable and emailable
- **Weekly Financial Summary** — per-term, per-class reporting across both schools

### Receipt Numbering Convention
- Labeo Montessori: `LMS-RCT-NNNN-YYYYMMDD`
- Labeo Comprehensive College: `LCC-RCT-NNNN-YYYYMMDD`

### Business Rules
- Each partial payment generates its **own** receipt (no combined/rolled-up receipts)
- Receipts are **permanent** — no voiding or editing once issued
- One bursar account per school; a Super Admin role has cross-school access
- Term selection is manual (not auto-detected by date)
- Students identified by name + class + section (not a numeric ID system)

---

## 2. Architecture

### Final Architecture (as deployed)
```
Browser (single HTML file)
 ├── Google OAuth 2.0 — authentication
 ├── Google Sheets API — student data, payment records, live "database"
 └── jsPDF — client-side PDF receipt generation
```

Everything — UI, logic, and API calls — lives in **one HTML file**, with Google Sheets acting as the live data store. There is no separate backend server to host or maintain.

### Original Architecture (superseded)
The project originally started as a more conventional stack:
- React / Next.js frontend
- Supabase (PostgreSQL) database
- Puppeteer for server-side PDF generation
- Nodemailer over Gmail SMTP for emailing receipts

This was scoped out in detail first, including board-level project documentation, before being replaced (see **Section 3** for why).

---

## 3. Key Issues Faced & Solutions

### Issue 1: Hosting/environment complexity vs. real-world constraints
**Problem:** The original React/Next.js + Supabase + Puppeteer stack required a Node.js server environment, a hosted PostgreSQL database, and server-side rendering for PDFs — none of which were easy to reliably host and maintain for a small school-admin use case, especially without dedicated DevOps support.

**Solution:** Pivoted to a **single-file HTML architecture** using Google Sheets as the live "database." This eliminated the need for a backend server entirely:
- Google Sheets replaced Supabase/PostgreSQL for storing student and payment data
- jsPDF replaced Puppeteer, moving PDF generation to the client side
- Google OAuth replaced a custom auth layer, reusing infrastructure the schools already trust (Gmail accounts)

This traded some scalability for **drastically simpler deployment and maintenance** — appropriate for the system's actual scale (two schools, a handful of bursars).

### Issue 2: Multi-school data isolation vs. shared access
**Problem:** Two schools (Labeo Montessori and Labeo Comprehensive College) needed separate day-to-day data handling — different bursars, different branding, different class structures — while still allowing a Super Admin to see across both.

**Solution:**
- Each school issues receipts under its own numbering prefix (`LMS-` vs `LCC-`)
- One bursar account is scoped per school
- A Super Admin role sits above both with cross-school visibility
- Class/section data is organized into separate tabs within the same Google Sheet, keyed to each school

### Issue 3: Receipt integrity for partial payments
**Problem:** Students often pay fees in installments. A naive system might update a single receipt per student per term, risking ambiguity about what was actually paid and when — a real problem for financial auditability.

**Solution:** Every partial payment generates its **own independent, permanent receipt**. Receipts are never edited or voided after issue, which keeps the payment trail auditable and matches how the school's bursars already thought about record-keeping on paper.

### Issue 4: Getting real data into a system built on test data
**Problem:** Development happened against test class tabs, not the real student rosters for either school.

**Solution (in progress):** Before go-live, the plan is to replace all test class tab data with the real, current student data for both institutions — done directly in Google Sheets rather than requiring a data migration script, since Sheets is the system of record.

### Issue 5: OAuth restricted to authorized users
**Problem:** Google OAuth apps in testing mode only allow pre-approved test users to log in — a blocker for the actual bursars who need day-to-day access.

**Solution (in progress):** Add each school's bursar Gmail account as an OAuth test user in the Google Cloud Console project, and update **Authorized JavaScript origins / redirect URIs** once the app has a live Netlify URL (rather than `localhost`).

---

## 4. Development Approach

The build followed a **mentor-guided, step-by-step process** rather than a single big build:
1. Requirements and business rules were nailed down first (payment types, receipt permanence, roles, numbering formats)
2. Board-level documentation was produced before writing code, to get sign-off on scope
3. Architecture was prototyped, tested against real hosting constraints, and revised once those constraints became clear
4. The system was rebuilt around the simpler single-file + Google Sheets approach
5. Features were implemented and verified in this order: Login → Student Lookup → Payment Entry → Receipt Generation → Weekly Financial Summary

---

## 5. Remaining Steps to Production

- [ ] Deploy the application to Netlify
- [ ] Update Google OAuth authorized origins with the live Netlify URL
- [ ] Replace test class tab data with real student data for both schools
- [ ] Add each school's bursar Gmail account as an OAuth test user

---

## 6. Tech Stack Summary

| Layer | Technology |
|---|---|
| Frontend | HTML/CSS/JS (single file) |
| Data storage | Google Sheets |
| Authentication | Google OAuth 2.0 |
| PDF generation | jsPDF |
| Hosting | Netlify |
| Branding | Wine + navy blue (Labeo Montessori), Cream + wine (Labeo Comprehensive College) |

---

*Documentation last updated: July 2026*
