<div align="center">

# 🎓 PlacementX

### Campus Placement Automation Platform

*Digitizing the entire campus placement lifecycle — from student profiles to offer letters.*

Built as a capstone project for **NMIMS University**

<br/>

![Status](https://img.shields.io/badge/status-single--college%20pilot-orange?style=for-the-badge)
![Web](https://img.shields.io/badge/web-deployed%20on%20Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![API](https://img.shields.io/badge/API-deployed%20on%20Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)
![Mobile](https://img.shields.io/badge/mobile-APK%20pending-yellow?style=for-the-badge&logo=expo&logoColor=white)

![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind%20v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Node](https://img.shields.io/badge/Node.js-20+-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Expo](https://img.shields.io/badge/Expo%2054-000020?style=flat-square&logo=expo&logoColor=white)

<br/>

[**Features**](#-features) ·
[**Architecture**](#-architecture) ·
[**Workflows**](#-workflows) ·
[**Data Model**](#-data-model) ·
[**Getting Started**](#-getting-started) ·
[**Deployment**](#-deployment) ·
[**Status**](#-project-status)

</div>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [User Roles](#-user-roles)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Workflows](#-workflows)
- [Data Model](#-data-model)
- [Repository Structure](#-repository-structure)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [Scripts](#-scripts)
- [API Overview](#-api-overview)
- [Business Rules](#-business-rules)
- [Deployment](#-deployment)
- [Project Status](#-project-status)
- [Known Limitations](#-known-limitations)
- [Contributing](#-contributing)

---

## 🌟 Overview

Campus placements at NMIMS were run on spreadsheets, email threads, and WhatsApp groups. **PlacementX** replaces that with one unified platform for the **Training & Placement Office (TPO)**, **students**, **coordinators**, and **recruiters**, on both web and mobile.

<table>
<tr>
<td width="25%" align="center">

### 🧑‍🎓 Students
Build profiles, discover eligible drives, apply, and track every application.

</td>
<td width="25%" align="center">

### 🏛️ Placement Cell
Run drives, verify students, import data, and watch live analytics.

</td>
<td width="25%" align="center">

### 🧑‍🏫 Coordinators
Manage students and verifications within their own department.

</td>
<td width="25%" align="center">

### 🤝 Recruiters
Submit drive details through a secure link, with no account needed.

</td>
</tr>
</table>

### The placement lifecycle at a glance

```mermaid
flowchart LR
    A["📥 Import<br/>students"] --> B["👤 Profile<br/>& verify"]
    B --> C["🏢 Create<br/>drive"]
    C --> D["✅ Eligibility<br/>check"]
    D --> E["📝 Apply"]
    E --> F["🎯 Selection<br/>rounds"]
    F --> G["📄 Offer<br/>letters"]
    G --> H["📊 Analytics<br/>& reports"]

    style A fill:#e0f2fe,stroke:#0284c7,color:#0c4a6e
    style B fill:#e0f2fe,stroke:#0284c7,color:#0c4a6e
    style C fill:#fef3c7,stroke:#d97706,color:#78350f
    style D fill:#fef3c7,stroke:#d97706,color:#78350f
    style E fill:#dcfce7,stroke:#16a34a,color:#14532d
    style F fill:#dcfce7,stroke:#16a34a,color:#14532d
    style G fill:#fce7f3,stroke:#db2777,color:#831843
    style H fill:#fce7f3,stroke:#db2777,color:#831843
```

> **⚠️ Status:** Single-college production pilot. Web is live on Vercel and the API on Render. Mobile source is complete and bundle-verified, but APK/device QA is pending. See [Project Status](#-project-status) and [Known Limitations](#-known-limitations).

---

## ✨ Features

| | Area | Highlights |
|---|------|-----------|
| 🧑‍🎓 | **Student portal** | Unified login · multi-step profile · semester-wise marks · separate 10th/12th/Degree PDF uploads · drive discovery · application tracking · interview calendar · 13-panel settings |
| 🏛️ | **Placement cell** | Drive wizard · eligibility engine · Excel/CSV bulk import · account provisioning · profile verification · update-request review · calendar · notification broadcasts |
| 📊 | **Analytics & reports** | Placement overview · department breakdown · year-over-year comparison · package analysis · company stats · application funnel · exportable Excel reports |
| 🤝 | **HR portal** | Token-based wizard · auto-saved drafts · approve / reject / request-changes workflow · public recruiter event view |
| 🔔 | **Notifications** | In-app · Firebase push (FCM) · Socket.io real-time · BullMQ queue · templates · scheduling |
| 🔐 | **Security** | Database-owned roles · 15-min JWTs · OTP password reset (HMAC, timing-safe) · rate limiting · private report storage |
| 🎨 | **Experience** | Light/dark theme · compact mode · responsive layouts · global loader · reduced-motion support |
| 🩺 | **Operations** | `/health` and `/health/ready` probes · graceful shutdown · CI with Prisma generation |

<details>
<summary><b>🧑‍🎓 Student settings — all 13 panels</b></summary>

<br/>

| Panel | Panel | Panel |
|-------|-------|-------|
| Account | Profile Preferences | Notifications |
| Security | Application Preferences | Calendar |
| Regional | Connected Devices | Privacy |
| Appearance | Danger Zone | Help & Support |

</details>

<details>
<summary><b>🚫 Removed features</b></summary>

<br/>

The earlier AI/ML features (success prediction, placement forecasting, resume parsing, embeddings, AI admin analytics) and the Python `ml-service` were **removed** to streamline the architecture.

</details>

---

## 👥 User Roles

| Role | Authentication | Access scope |
|------|----------------|--------------|
| 🧑‍🎓 **STUDENT** | Firebase credential → API JWT | `/student/*` |
| 🏛️ **SUPER_ADMIN** | Firebase credential → API JWT | `/admin/*` (institution-wide) |
| 🧑‍🏫 **COORDINATOR** | Firebase credential → API JWT | Limited `/admin/*` (own department) |
| 🤝 **HR / Recruiter** | Invitation token (no account) | `/hr-drive/:token` |
| 👤 **Guest** | None | `/login` and public pages |

```mermaid
flowchart TD
    U(["Request arrives"]) --> G{"Has valid<br/>JWT or token?"}
    G -- "No" --> PUB["Public pages<br/>/login, /about, /faq ..."]
    G -- "HR invitation token" --> HRP["HR portal<br/>/hr-drive/:token"]
    G -- "JWT" --> R{"Role reloaded<br/>from PostgreSQL"}
    R -- "STUDENT" --> S["/student/*"]
    R -- "SUPER_ADMIN" --> A["/admin/*<br/>full access"]
    R -- "COORDINATOR" --> C["/admin/students/*<br/>department-scoped"]

    style PUB fill:#f3f4f6,stroke:#6b7280
    style HRP fill:#fef3c7,stroke:#d97706
    style S fill:#dcfce7,stroke:#16a34a
    style A fill:#fee2e2,stroke:#dc2626
    style C fill:#e0f2fe,stroke:#0284c7
```

<details>
<summary><b>Permission matrix</b></summary>

<br/>

| Capability | Student | Coordinator | Super Admin | HR |
|------------|:------:|:-----------:|:-----------:|:--:|
| Own profile and applications | ✅ | ❌ | ❌ | ❌ |
| Apply to drives | ✅ | ❌ | ❌ | ❌ |
| Manage students (own department) | ❌ | ✅ | ✅ | ❌ |
| Verify profiles / update requests | ❌ | ✅ | ✅ | ❌ |
| Drive administration | ❌ | ❌ | ✅ | ❌ |
| Bulk import and provisioning | ❌ | ❌ | ✅ | ❌ |
| Analytics and reports | ❌ | ❌ | ✅ | ❌ |
| Broadcasts and calendar | ❌ | ❌ | ✅ | ❌ |
| Coordinator management and settings | ❌ | ❌ | ✅ | ❌ |
| Submit drive details via link | ❌ | ❌ | ❌ | ✅ |

</details>

---

## 🧰 Tech Stack

<table>
<tr>
<td valign="top" width="33%">

### 🌐 Web
`apps/web`

- React 18 + TypeScript
- Vite
- Tailwind CSS v4
- shadcn/ui
- Zustand
- TanStack Query
- React Router v7
- React Hook Form + Zod
- Recharts · FullCalendar
- Framer Motion
- Socket.io Client
- Firebase SDK

</td>
<td valign="top" width="33%">

### 📱 Mobile
`apps/mobile`

- React Native (Expo 54)
- TypeScript
- React Navigation
- Zustand
- TanStack Query
- expo-notifications
- expo-secure-store
- Socket.io Client
- Firebase SDK

</td>
<td valign="top" width="33%">

### ⚙️ API
`apps/api`

- Node.js ≥ 20 + Express
- TypeScript
- Prisma + PostgreSQL
- Firebase Admin
- JWT
- BullMQ + Redis
- Socket.io
- Zod · ExcelJS
- Nodemailer (SMTP / Brevo)
- Supabase Storage

</td>
</tr>
</table>

**Infrastructure:** Vercel · Render (Singapore) · Supabase · Firebase · Brevo · GitHub Actions · Docker Compose (local PostgreSQL)

---

## 🏗️ Architecture

### System architecture

```mermaid
flowchart TB
    subgraph Clients["🖥️ Clients"]
        Web["React Web App<br/>Vite · port 5173"]
        Mobile["React Native App<br/>Expo"]
        HR["HR Portal<br/>token-based"]
    end

    subgraph Backend["⚙️ Backend · Express API · port 5000"]
        MW["Middleware<br/>JWT auth · authorize · rate limit"]
        CTRL["Controllers"]
        SVC["Services<br/>eligibility · notifications · email · reports"]
        SIO["Socket.io"]
        BQ["BullMQ workers"]
    end

    subgraph Data["🗄️ Data and external services"]
        PG[("PostgreSQL<br/>Supabase")]
        FB["Firebase<br/>Auth · Storage · FCM"]
        RD[("Redis<br/>Valkey 8")]
        SB["Supabase Storage<br/>private reports bucket"]
        SMTP["Brevo SMTP"]
    end

    Web -->|"REST + WebSocket"| MW
    Mobile -->|"REST + WebSocket"| MW
    HR -->|"REST"| MW
    MW --> CTRL --> SVC
    SVC --> PG
    SVC --> FB
    SVC --> SB
    SVC --> SMTP
    SVC --> BQ
    BQ --- RD
    BQ -->|"push"| FB
    SIO -.->|"live events"| Web
    SIO -.->|"live events"| Mobile

    style Clients fill:#eff6ff,stroke:#3b82f6
    style Backend fill:#fefce8,stroke:#eab308
    style Data fill:#f0fdf4,stroke:#22c55e
```

The API follows a layered pattern:

```
Routes → Middleware (Auth + Authorization) → Controllers → Services → Prisma → PostgreSQL
```

### Request data flow

```mermaid
flowchart LR
    UI["React component"] --> F["React Hook Form<br/>+ Zod schema"]
    F --> Q["TanStack Query<br/>cache · loading · errors"]
    Q --> AX["Axios service"]
    AX --> API["Express route"]
    API --> AUTH["JWT auth +<br/>role authorize"]
    AUTH --> C["Controller"]
    C --> S["Service"]
    S --> P["Prisma"]
    P --> DB[("PostgreSQL")]
    S -.-> E1["Socket.io event"]
    S -.-> E2["BullMQ job → FCM push"]
```

### Authentication

```mermaid
sequenceDiagram
    autonumber
    participant U as User
    participant W as Web / Mobile
    participant FB as Firebase Auth
    participant A as API
    participant DB as PostgreSQL

    U->>W: Email + password
    W->>FB: Sign in
    FB-->>W: Firebase ID token
    W->>A: POST /api/auth/firebase-login
    A->>FB: Verify ID token
    A->>DB: Load user and database-owned role
    Note over A: Browser-supplied roles are ignored
    A->>A: Issue short-lived JWT (15 min)
    A-->>W: token + user
    W->>W: Persist in Zustand store

    loop Every protected request
        W->>A: Authorization: Bearer token
        A->>A: Verify JWT
        A->>DB: Reload role and coordinator department
        A->>A: Enforce role and department scope
        A-->>W: Protected resource
    end
```

Login **fails closed**: if verification fails, there is no offline or client-selected role fallback. Demo accounts in `DEMO_EMAIL_ALLOWLIST` may sign in without Firebase email verification.

### Notification pipeline

```mermaid
flowchart LR
    EVT["Event<br/>drive published · status change · broadcast"] --> NS["Notification service"]
    NS --> DBN[("Notification table")]
    NS --> Q{"Redis<br/>available?"}
    Q -- "Yes" --> BQ["BullMQ queue"]
    Q -- "No" --> FALL["Graceful fallback<br/>direct processing"]
    BQ --> W["Worker<br/>retries on failure"]
    FALL --> W
    W --> PUSH["FCM push"]
    W --> EMAIL["Email"]
    NS --> SOCK["Socket.io<br/>real-time delivery"]
    SOCK --> CLIENT["Web and mobile clients"]
    PUSH --> CLIENT
```

---

## 🔄 Workflows

### Student onboarding

```mermaid
flowchart TD
    A["Admin imports Excel / CSV"] --> B["ImportedStudent records created"]
    B --> C["Admin triggers provisioning"]
    C --> D["User + StudentProfile accounts created"]
    D --> E["Student receives credentials"]
    E --> F["First login"]
    F --> G["Forced password change<br/>mustChangePassword = true"]
    G --> H["Student completes multi-step profile"]
    H --> I["Submit for verification"]
    I --> J{"Admin review"}
    J -- "Verified" --> K["Profile locked 🔒"]
    J -- "Rejected" --> H
    K --> L["Changes need an update request"]
    L --> M{"Admin approves?"}
    M -- "Yes" --> H
    M -- "No" --> K

    style K fill:#dcfce7,stroke:#16a34a
    style G fill:#fef3c7,stroke:#d97706
```

### Profile status

```mermaid
stateDiagram-v2
    [*] --> NOT_COMPLETED
    NOT_COMPLETED --> PENDING_VERIFICATION: Student submits
    PENDING_VERIFICATION --> VERIFIED: Admin approves
    PENDING_VERIFICATION --> REJECTED: Admin rejects
    REJECTED --> PENDING_VERIFICATION: Student resubmits
    VERIFIED --> [*]
    note right of VERIFIED
        Locked. Edits require a
        ProfileUpdateRequest
    end note
```

### Placement drive lifecycle

Drives can be created directly by the admin (**Method A**) or collaboratively with HR (**Method B**).

```mermaid
stateDiagram-v2
    [*] --> WAITING_FOR_HR: Method B (admin sends HR link)
    [*] --> DRAFT: Method A (admin creates directly)
    WAITING_FOR_HR --> DRAFT: HR submits wizard
    DRAFT --> UNDER_REVIEW: Submitted for review
    UNDER_REVIEW --> DRAFT: Changes requested
    UNDER_REVIEW --> ACTIVE: Approved and published
    ACTIVE --> CLOSED: Applications closed
    CLOSED --> COMPLETED: Rounds and offers done
    COMPLETED --> [*]
```

### HR collaboration

```mermaid
sequenceDiagram
    autonumber
    actor Admin as 🏛️ Admin
    participant API as API
    actor HR as 🤝 HR / Recruiter
    participant S as Students

    Admin->>API: POST /hr/generate (drive, HR email)
    API-->>Admin: Secure invitation link (expiring)
    Admin->>HR: Sends link by email
    HR->>API: POST /hr/validate (token)
    API-->>HR: Workspace unlocked
    loop While filling the wizard
        HR->>API: PUT /hr/draft (auto-save)
    end
    HR->>API: POST /hr/submit
    API-->>Admin: Drive moves to review
    alt Approved
        Admin->>API: POST /admin/drives/:id/approve
        API-->>S: Drive ACTIVE, notification sent
    else Changes requested
        Admin->>API: POST /admin/drives/:id/request-changes
        API-->>HR: Link reopened for edits
    else Rejected
        Admin->>API: POST /admin/drives/:id/reject
    end
```

HR links carry an `expiresAt` timestamp, and expiry is enforced in **every** drive state, even after publication.

### Student application

```mermaid
flowchart TD
    S["Student clicks Apply"] --> E{"Eligibility engine"}
    E -- "Fails" --> X["Blocked with reason codes<br/>CGPA · backlogs · branch · gap ..."]
    E -- "Passes" --> T["Begin SERIALIZABLE transaction"]
    T --> D1{"Already applied?"}
    D1 -- "Yes" --> X2["Rejected: duplicate"]
    D1 -- "No" --> D2{"Drive capacity<br/>available?"}
    D2 -- "No" --> X3["Rejected: drive full"]
    D2 -- "Yes" --> D3{"Under global<br/>application limit?"}
    D3 -- "No" --> X4["Rejected: limit reached"]
    D3 -- "Yes" --> D4{"Live offer<br/>limit OK?"}
    D4 -- "No" --> X5["Rejected: offer limit"]
    D4 -- "Yes" --> OK["Commit application<br/>with eligibility snapshot"]

    style OK fill:#dcfce7,stroke:#16a34a
    style X fill:#fee2e2,stroke:#dc2626
    style X2 fill:#fee2e2,stroke:#dc2626
    style X3 fill:#fee2e2,stroke:#dc2626
    style X4 fill:#fee2e2,stroke:#dc2626
    style X5 fill:#fee2e2,stroke:#dc2626
```

### Application status

```mermaid
stateDiagram-v2
    [*] --> APPLIED
    APPLIED --> SHORTLISTED
    APPLIED --> REJECTED
    SHORTLISTED --> INTERVIEWED
    SHORTLISTED --> REJECTED
    INTERVIEWED --> OFFERED
    INTERVIEWED --> REJECTED
    OFFERED --> [*]
    REJECTED --> [*]
```

### OTP password reset

```mermaid
sequenceDiagram
    autonumber
    actor U as User
    participant W as Web
    participant A as API
    participant DB as PostgreSQL
    participant M as Brevo SMTP
    participant FB as Firebase Auth

    U->>W: Open /forgot-password and enter email
    W->>A: POST /auth/password-reset/request
    A->>A: Generate 6-digit OTP and HMAC-hash it
    A->>DB: Store challenge (expires in 5 min)
    A->>M: Send OTP email
    M-->>U: OTP delivered

    U->>W: Enter OTP
    W->>A: POST /auth/password-reset/verify
    A->>DB: Load challenge
    A->>A: Timing-safe compare (max 5 attempts)
    A-->>W: Single-use resetGrant (10 min)

    U->>W: Choose new password
    W->>A: POST /auth/password-reset/confirm
    A->>DB: Update password and invalidate all challenges
    A->>FB: Update Firebase Auth password
    A-->>W: Success
```

| Safeguard | Value |
|-----------|-------|
| OTP lifetime | 5 minutes |
| Reset grant lifetime | 10 minutes, single use |
| Resend cooldown | 60 seconds |
| Max failed attempts | 5 per challenge |
| Storage | HMAC-SHA-256 hash with `PASSWORD_RESET_SECRET` |
| Comparison | Constant-time |

---

## 🗄️ Data Model

Schema source of truth: [`apps/api/prisma/schema.prisma`](apps/api/prisma/schema.prisma)

### Core entities

```mermaid
erDiagram
    USER ||--o| STUDENT_PROFILE : has
    USER ||--o| ADMIN_PROFILE : has
    USER ||--o| COORDINATOR_PROFILE : has
    USER ||--o{ DEVICE_TOKEN : registers
    USER ||--o{ NOTIFICATION : receives
    USER ||--o| NOTIFICATION_PREFERENCE : configures
    USER ||--o{ PASSWORD_RESET_CHALLENGE : requests

    COMPANY ||--o{ PLACEMENT_DRIVE : hosts
    PLACEMENT_DRIVE ||--o{ DRIVE_APPLICATION : receives
    PLACEMENT_DRIVE ||--o{ SELECTION_ROUND : contains
    PLACEMENT_DRIVE ||--o{ HR_INVITATION_LINK : issues
    PLACEMENT_DRIVE ||--o{ DRIVE_AUDIT_LOG : records

    STUDENT_PROFILE ||--o{ DRIVE_APPLICATION : submits
    STUDENT_PROFILE ||--o{ PROFILE_UPDATE_REQUEST : requests
    STUDENT_PROFILE ||--o{ PROFILE_AUDIT_LOG : tracked_by
    STUDENT_PROFILE ||--o{ STUDENT_DOCUMENT : uploads
    STUDENT_PROFILE ||--o| STUDENT_PREFERENCE : sets

    DRIVE_APPLICATION ||--o| OFFER_LETTER : yields
    DRIVE_APPLICATION ||--o{ APPLICATION_ROUND_RESULT : scored_in
    SELECTION_ROUND ||--o{ APPLICATION_ROUND_RESULT : produces

    USER {
        string id PK
        string email
        string role
        string firebaseUid
        boolean mustChangePassword
    }
    STUDENT_PROFILE {
        string id PK
        string userId FK
        float cgpa
        string branch
        string profileStatus
        boolean isProfileComplete
    }
    COORDINATOR_PROFILE {
        string id PK
        string userId FK
        string department
    }
    COMPANY {
        string id PK
        string name
        string industry
        string hrEmail
    }
    PLACEMENT_DRIVE {
        string id PK
        string companyId FK
        string status
        string jobRole
    }
    DRIVE_APPLICATION {
        string id PK
        string driveId FK
        string studentId FK
        string status
        json eligibilitySnapshot
    }
    OFFER_LETTER {
        string id PK
        string applicationId FK
        string offerStatus
    }
    PASSWORD_RESET_CHALLENGE {
        string id PK
        string userId FK
        string otpHash
        string status
        int failedAttempts
    }
```

> `DriveApplication` has a unique constraint on `(driveId, studentId)`, so a student can apply to a drive only once.

<details>
<summary><b>📚 Full entity catalogue</b></summary>

<br/>

| Group | Entities |
|-------|----------|
| **Accounts** | `User`, `AdminProfile`, `CoordinatorProfile`, `StudentProfile`, `AccountActivationToken`, `PasswordResetChallenge` |
| **Drives** | `Company`, `PlacementDrive`, `SelectionRound`, `DriveApplication`, `ApplicationRoundResult`, `OfferLetter`, `DriveAuditLog`, `HrInvitationLink` |
| **Policy & eligibility** | `PlacementPolicyVersion`, `EligibilityEvaluation`, `AttendanceExceptionReview` |
| **Student data** | `ImportedStudent`, `StudentDocument`, `StudentPreference`, `ProfileUpdateRequest`, `ProfileAuditLog` |
| **Notifications** | `Notification`, `NotificationCampaign`, `NotificationTemplate`, `NotificationPreference`, `DeviceToken` |
| **Reports** | `ReportTemplate`, `ReportExportHistory`, `ScheduledReport` |
| **Configuration** | `SystemSetting`, `SettingAuditLog`, `AcademicYear`, `Semester`, `CustomCalendarEvent` |

</details>

---

## 📁 Repository Structure

```
PlacementX/
├── apps/
│   ├── api/                  ⚙️  Express + Prisma backend
│   │   ├── prisma/           │   schema.prisma + migrations
│   │   └── src/              │   config · controllers · middlewares · routes
│   │                         │   services · socket · utils
│   ├── web/                  🌐  React (Vite) web app
│   │   └── src/features/     │   admin · auth · hr-portal · notifications · public · student
│   └── mobile/               📱  React Native (Expo) app
├── packages/                 📦  Shared workspace packages
│                                 types · ui · utils · validation · firebase · config ...
├── Student_data/             📊  Excel files for student import
├── docs/                     📚  Audits, deployment notes, mobile docs
├── docker-compose.yml        🐳  Local PostgreSQL
├── .env.example              🔑  Environment template
├── ARCHITECTURE.md           🏗️  System architecture notes
└── package.json              npm workspaces root
```

<details>
<summary><b>⚠️ Files to modify with care</b></summary>

<br/>

| File | Why |
|------|-----|
| `apps/api/prisma/schema.prisma` | Database source of truth; changes need a migration |
| `apps/web/src/routes/index.tsx` | Central routing; route changes require guard updates |
| `apps/web/src/stores/authStore.ts` | Auth state used by every protected route |
| `apps/api/src/middlewares/auth.middleware.ts` | JWT verification; changes affect all protected endpoints |
| `packages/types/` | Shared by web and mobile |

</details>

---

## 🚀 Getting Started

### Prerequisites

| Requirement | Notes |
|-------------|-------|
| Node.js ≥ 20, npm ≥ 10 | Required |
| Firebase project | Auth, Storage, and FCM enabled |
| Supabase project | Or a local PostgreSQL instance |
| Docker | Optional, for local PostgreSQL |
| Redis | Optional locally, required for production queues |

### Setup flow

```mermaid
flowchart LR
    A["git clone"] --> B["npm install"]
    B --> C["cp .env.example<br/>.env.local"]
    C --> D["Start PostgreSQL<br/>Docker or Supabase"]
    D --> E["prisma db push<br/>dev only"]
    E --> F["npm run db:seed"]
    F --> G["npm run dev"]
    G --> H(["🌐 localhost:5173<br/>⚙️ localhost:5000"])

    style H fill:#dcfce7,stroke:#16a34a
```

### Commands

```bash
# 1. Clone and install
git clone <repository-url>
cd PlacementX
npm install

# 2. Configure environment (fill in Firebase, Supabase, JWT, password-reset secrets)
cp .env.example .env.local

# 3. Database
docker-compose up -d            # Option A: local PostgreSQL
                                # Option B: set DATABASE_URL / DIRECT_URL for Supabase
cd apps/api
npx prisma db push              # disposable dev databases only
npm run db:seed                 # seeds an admin and a test student
cd ../..

# 4. Run API (5000) + Web (5173)
npm run dev
```

```bash
# Run apps individually
npm run dev --workspace=@placementx/api
npm run dev --workspace=@placementx/web

# Mobile (Expo)
cd apps/mobile && npm start
```

> On Windows use `run.bat`; on Unix use `run.sh`.
>
> 🔑 Seed credentials live in `apps/api/src/seed.ts` and `login_credentials.md`. They are for **local development only**. Never use them in production. For persistent or deployed databases, use committed migrations (`npm run db:migrate:deploy`) instead of `db push`.

---

## 🔐 Environment Variables

Copy `.env.example` to `.env.local` (gitignored). **Never commit real secrets.**

| Group | Variables |
|-------|-----------|
| 🗄️ **Database** | `DATABASE_URL` · `DIRECT_URL` |
| 🔥 **Firebase (client)** | `VITE_FIREBASE_API_KEY` · `VITE_FIREBASE_AUTH_DOMAIN` · `VITE_FIREBASE_PROJECT_ID` · `VITE_FIREBASE_STORAGE_BUCKET` · `VITE_FIREBASE_MESSAGING_SENDER_ID` · `VITE_FIREBASE_APP_ID` |
| 🔥 **Firebase (server)** | `FIREBASE_WEB_API_KEY` · `FIREBASE_DATABASE_URL` |
| 🔑 **Auth** | `JWT_SECRET` · `JWT_ACCESS_EXPIRES_IN` (default `15m`) · `JWT_ISSUER` · `JWT_AUDIENCE` · `PASSWORD_RESET_SECRET` (≥ 32 chars) |
| ✉️ **Email** | `SMTP_HOST` · `SMTP_PORT` · `SMTP_USER` · `SMTP_PASSWORD` · `EMAIL_FROM` · `EMAIL_FROM_NAME` |
| 📮 **Queues** | `REDIS_URL` · `REDIS_REQUIRED` (default `false`) |
| 🪣 **Storage** | `SUPABASE_SERVICE_ROLE_KEY` · `SUPABASE_STORAGE_BUCKET` · `SUPABASE_REPORTS_BUCKET` |
| 🛡️ **Access control** | `DEMO_EMAIL_ALLOWLIST` · `OFFICIAL_STUDENT_EMAIL_DOMAINS` · `CORS_ORIGINS` · `TRUST_PROXY` |
| 🚦 **Rate limiting** | `AUTH_RATE_LIMIT_WINDOW_MS` (default 15 min) · `AUTH_RATE_LIMIT_MAX` (default 10) |
| 🌍 **General** | `FRONTEND_URL` · `PORT` (default `5000`) |

Standalone mobile builds require an explicit `EXPO_PUBLIC_API_URL`.

---

## 🛠️ Scripts

| Command | Scope | Description |
|---------|-------|-------------|
| `npm run dev` | Root | Start API and web together |
| `npm run build` | Root | Build all workspaces |
| `npm run lint` | Root | Lint all workspaces |
| `npm run type-check` | Root | TypeScript checks |
| `npm run format` / `format:check` | Root | Prettier |
| `npm run seed` | Root | Seed the database |
| `npm run db:push` | `apps/api` | Dev-only schema sync |
| `npm run db:migrate:deploy` | `apps/api` | Apply committed migrations |
| `npm run db:migrate:status` | `apps/api` | Inspect migration state |
| `npm run db:studio` | `apps/api` | Prisma Studio |
| `npm run db:seed` | `apps/api` | Seed the database |

---

## 🔌 API Overview

**Base URL:** `http://localhost:5000/api` · **Auth:** `Authorization: Bearer <JWT>`

```mermaid
flowchart LR
    API(("/api")) --> AUTH["/auth"]
    API --> ADMIN["/admin"]
    API --> HRR["/hr"]
    API --> REC["/recruiter"]
    API --> STU["/student"]
    API --> NOT["/notifications"]
    API --> PUB["/public"]

    ADMIN --> DR["/drives"]
    ADMIN --> AN["/analytics"]
    ADMIN --> RP["/reports"]
    ADMIN --> ST["/settings"]
    STU --> SS["/settings"]

    H["/health"] --- HR2["/health/ready"]
```

| Prefix | Description | Auth |
|--------|-------------|------|
| `/api/auth` | Login, register, Firebase login, change password, current user, OTP password reset | Mixed |
| `/api/admin` | Dashboard, students, coordinators, calendar, import, provisioning, verifications, update requests | Admin |
| `/api/admin/drives` | Drive CRUD, applications, HR drive review | Mixed |
| `/api/admin/analytics` | Placement stats and insights | Admin |
| `/api/admin/reports` | Report generation, download, history | Admin |
| `/api/admin/settings` | System settings | Admin |
| `/api/hr` | Link generation, validation, drafts, submission | Admin / token |
| `/api/recruiter` | Event view, shortlisting, interviews | Token |
| `/api/student` | Profile, applications, interviews, documents | Student |
| `/api/student/settings` | Preferences, privacy, devices, support, deactivation, data export | Student |
| `/api/notifications` | Notifications, preferences, devices, broadcast, scheduling | JWT |
| `/api/public` | Public placement stats | None |
| `/health` · `/health/ready` | Liveness and readiness probes | None |

<details>
<summary><b>Health endpoints</b></summary>

<br/>

| Endpoint | Success | Failure | Checks |
|----------|---------|---------|--------|
| `GET /health` | `200 {"status":"ok"}` | n/a | Express process only |
| `GET /health/ready` | `200 {"status":"ready"}` | `503 {"status":"not_ready"}` | Redis PING with a 2 s timeout |

Neither endpoint exposes credentials, internal addresses, or stack traces.

</details>

---

## 📜 Business Rules

> These rules must not be broken accidentally during development.

| # | Rule | Detail |
|---|------|--------|
| 1 | 🔒 **Profile lock** | Verified profiles are read-only; changes go through a `ProfileUpdateRequest` |
| 2 | ✅ **Eligibility** | Min CGPA · allowed branches · current and total backlogs · year gap · semester · passing year · gender · required resume/portfolio/GitHub/LinkedIn |
| 3 | 1️⃣ **Unique application** | One application per student per drive |
| 4 | ⚛️ **Safe concurrency** | Applications use a serializable transaction (duplicate, capacity, limit, and offer rechecks) |
| 5 | 🔑 **Forced password change** | Provisioned accounts must change password on first login |
| 6 | ⏳ **HR link expiry** | Enforced in every drive state |
| 7 | 🛡️ **Role access** | `SUPER_ADMIN` is institution-wide; `COORDINATOR` is department-scoped |
| 8 | 🎯 **Offer limits** | Multiple offers disallowed; applications per student capped (default 5) via settings |

---

## ☁️ Deployment

```mermaid
flowchart LR
    DEV["👩‍💻 Developer"] -->|"git push main"| GH["GitHub"]
    GH --> CI["GitHub Actions<br/>Prisma generate · lint · type-check · tests"]
    CI -->|"auto-deploy"| VC["▲ Vercel<br/>Web app · SPA routing"]
    CI -->|"auto-deploy"| RN["Render · Singapore<br/>Express API"]

    RN --> KV[("Render Key Value<br/>Valkey 8")]
    RN --> SP[("Supabase<br/>PostgreSQL + Storage")]
    RN --> FBS["Firebase<br/>Auth · FCM"]
    RN --> BR["Brevo<br/>SMTP"]
    VC -->|"HTTPS"| RN

    USER["🧑‍🎓 Users"] --> VC

    style VC fill:#f3f4f6,stroke:#111827
    style RN fill:#d1fae5,stroke:#059669
```

| Service | Platform | Notes |
|---------|----------|-------|
| 🌐 Web | Vercel | `apps/web/vercel.json` SPA routing, auto-deploys from `main` |
| ⚙️ API | Render (Singapore) | Free tier, auto-deploys from `main` |
| 📮 Redis | Render Key Value | Valkey 8, private network |
| 🗄️ Database | Supabase | PostgreSQL via Prisma |
| 🔥 Auth / FCM | Firebase | Google Cloud |
| ✉️ Email | Brevo | SMTP via Nodemailer |

### Release checklist

- [ ] Provision PostgreSQL/Supabase, Redis, Firebase, and API/web runtimes
- [ ] Create a **private** Supabase bucket named `generated-reports`
- [ ] Set production secrets: `JWT_SECRET`, `PASSWORD_RESET_SECRET`, Firebase Admin credentials, Redis, Supabase, SMTP
- [ ] New database: run `npm run db:migrate:deploy`
- [ ] Existing `db push` database: back up, verify it matches the baseline, then mark `20260919000000_baseline` as applied with `prisma migrate resolve`. **Never run the baseline SQL on a populated database.**
- [ ] Verify `/health` and `/health/ready`
- [ ] Run production builds, tests, and live end-to-end checks before admitting users

> 💤 Render's free tier sleeps after 15 minutes of inactivity (30–60 s cold start). See `docs/RENDER_FREE_TIER_KEEPALIVE.md`.

---

## 📈 Project Status

```mermaid
flowchart LR
    subgraph DONE["✅ Completed"]
        D1["Auth and RBAC"]
        D2["OTP password reset"]
        D3["Profiles and verification"]
        D4["Drives and HR portal"]
        D5["Eligibility and applications"]
        D6["Notifications"]
        D7["Analytics and reports"]
        D8["Student settings"]
        D9["Health and CI"]
        D10["Vercel and Render deploy"]
    end
    subgraph WIP["🚧 In progress"]
        W1["Integration and E2E coverage"]
        W2["Monitoring, backups, alerting"]
    end
    subgraph TODO["⏳ Pending"]
        P1["Multi-tenant isolation"]
        P2["Firebase to PostgreSQL migration"]
        P3["Deployed E2E testing"]
        P4["Render keepalive automation"]
    end
    subgraph BLOCK["⛔ Blocked"]
        B1["Mobile release<br/>APK toolchain · device QA · push credentials"]
    end

    style DONE fill:#dcfce7,stroke:#16a34a
    style WIP fill:#fef3c7,stroke:#d97706
    style TODO fill:#e0f2fe,stroke:#0284c7
    style BLOCK fill:#fee2e2,stroke:#dc2626
```

| Area | Status |
|------|:------:|
| Web application | ✅ Deployed |
| API | ✅ Deployed |
| Password reset and email | ✅ Operational |
| Health monitoring | ✅ Live |
| Automated tests | 🟡 8 API test files, E2E expanding |
| Mobile app | ⚠️ Source and bundle verified, APK blocked |
| Multi-tenancy | ❌ Not started |

---

## ⚠️ Known Limitations

| Issue | Severity | Notes |
|-------|:--------:|-------|
| **No multi-tenant isolation** | 🔴 Critical for SaaS | Single-college design. Tenant scoping is needed across DB, storage, queues, and Socket.io before serving multiple colleges |
| **Mobile release incomplete** | 🟠 High | Source, TypeScript, contract tests, and Android export pass; no APK or device-install claim is made |
| **Render cold starts** | 🟡 Medium | 30–60 s first request after idle on the free tier |
| **Large Excel chunk** | 🟡 Medium | ~949 KB in the web build; load spreadsheet features on demand |
| **Limited test coverage** | 🟡 Medium | Broader auth, authorization, import, report, and E2E coverage needed |
| **Dual Firebase / PostgreSQL** | 🟡 Medium | Firebase remains for Auth/FCM while PostgreSQL holds app data |
| **SMTP dependency** | 🟢 Low | Production password reset depends on Brevo availability |

---

## 🤝 Contributing

**Before changing code**

1. Read `project_context.md` and `ARCHITECTURE.md`
2. Check `apps/api/prisma/schema.prisma` before any database change
3. Follow the controller → service → Prisma pattern and the feature-based layout in `apps/web/src/features/`
4. Use Prisma for data access, Zod for validation, TanStack Query for fetching, and shadcn/ui for components

**After changing code**

```bash
npm run type-check
npm run lint
```

If the Prisma schema changed, create and review a migration (use `db:push` only on disposable databases), then update `project_context.md` and its change log.

---

## 📄 License

Built as a capstone project for NMIMS University. Add license terms here if the repository is made public.

<div align="center">

<br/>

**PlacementX** · Made for NMIMS University 🎓

</div>
