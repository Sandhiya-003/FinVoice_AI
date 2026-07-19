<div align="center">

# 🎙️ FinVoice AI
### 💳 Voice-First Banking for Inclusive Financial Access

[![Frontend](https://img.shields.io/badge/Frontend-React%2019-61DAFB?logo=react&logoColor=black)](#-tech-stack)
[![Build](https://img.shields.io/badge/Build-Vite-646CFF?logo=vite&logoColor=white)](#-tech-stack)
[![Backend](https://img.shields.io/badge/Backend-FastAPI-009688?logo=fastapi&logoColor=white)](#-tech-stack)
[![Database](https://img.shields.io/badge/Database-SQLite-07405E?logo=sqlite&logoColor=white)](#-tech-stack)
[![AI Model](https://img.shields.io/badge/LLM-Groq%20API-F55036?logo=groq&logoColor=white)](#-tech-stack)
[![Speech](https://img.shields.io/badge/Text--to--Speech-gTTS-4285F4?logo=googletranslate&logoColor=white)](#-tech-stack)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](#)
[![Status](https://img.shields.io/badge/Status-Active%20Development-yellow.svg)](#)

*Making digital banking accessible through voice, AI, and inclusive design.*

</div>

---

## 📖 Overview

**FinVoice AI** is an AI-powered, multilingual banking assistant built for people digital banking traditionally leaves behind:

| 👥 Target User | Why They're Underserved |
|---|---|
| 🌾 Rural users | Limited exposure to app-based banking UX |
| 👵 Elderly citizens | Small text, complex menus, unfamiliar navigation |
| 👨‍🦯 Visually impaired users | Screen-heavy interfaces with poor accessibility |
| 📖 Low-literacy users | Reading/typing is a hard barrier, not a minor one |
| 📱 First-time smartphone users | No prior mental model of app navigation |

Instead of navigating menus, forms, and small buttons, users simply **speak** their banking request in their preferred language and receive a **spoken** response back.

---

## 🎯 Problem Statement

Traditional banking apps assume a level of literacy, dexterity, and digital familiarity that a large share of Indian users don't have — which quietly locks them out of digital financial inclusion.

| ❌ Barrier in Existing Apps | ✅ How FinVoice AI Solves It |
|---|---|
| Requires reading | Fully voice-driven interaction, no reading needed |
| Requires typing | Speak commands naturally instead of typing |
| Complex, multi-step navigation | Single conversational flow powered by intent detection |
| Password management | Biometric authentication (fingerprint, face — planned) |
| English/limited language support | Native support for Tamil, Hindi, Telugu, and English |
| No feedback on errors | Voice confirmation at every step of a transaction |

---

## 🚀 Key Features

- **🎤 Voice Banking** — balance enquiry, fund transfer, loan status, transaction history, voice-driven navigation
- **🌍 Multilingual Support** — Tamil · Hindi · Telugu · English
- **🤖 AI-Powered Assistance** — natural language understanding, intent detection, context-aware, conversational
- **🔒 Secure Authentication** — fingerprint verification, transaction confirmation, beneficiary verification, face authentication (planned)
- **♿ Accessibility-Focused Design** — large UI components, voice navigation, screen-reader friendly, high-contrast support

**Architecture highlights:**
- Voice-first banking assistant designed specifically for unbanked and underserved users
- Full audio processing pipeline: speech → text → AI response → audio
- RESTful API with three main route modules: `auth`, `banking`, `voice`
- Frontend (Vite dev server on `localhost:5173`) connects to the backend via CORS

---

## 🏗️ Architecture

```mermaid
flowchart TD
    A["🎙️ User Voice Input"] --> B["Speech-to-Text — Whisper<br/><i>(pending implementation)</i>"]
    B --> C["Groq API<br/>LLM Intent Recognition"]
    C --> D["FastAPI Backend"]
    D --> E["Auth Routes"]
    D --> F["Banking Routes"]
    D --> G["Voice Routes"]
    E --> H["SQLAlchemy ORM"]
    F --> H
    G --> H
    H --> I[("SQLite<br/>(configurable via DATABASE_URL)")]
    I --> J["Response Generation"]
    J --> K["gTTS<br/>Text-to-Speech"]
    K --> L["🔊 Voice Response to User"]
```

---

## 🗄️ Database Schema

```mermaid
erDiagram
    USER ||--o{ ACCOUNT : owns
    USER ||--o{ VOICE_SESSION : initiates
    USER ||--o{ BENEFICIARY : registers
    ACCOUNT ||--o{ TRANSACTION : records
    ACCOUNT ||--o{ LOAN : holds
    ACCOUNT ||--o{ BENEFICIARY : linked_to

    USER {
        int user_id PK
        string full_name
        string preferred_language
        string biometric_status
    }
    ACCOUNT {
        int account_id PK
        int user_id FK
        string bank_details
        decimal balance
    }
    TRANSACTION {
        int transaction_id PK
        int account_id FK
        decimal amount
        string payment_status
        timestamp transaction_date
    }
    LOAN {
        int loan_id PK
        int account_id FK
        decimal emi_amount
        string loan_status
    }
    VOICE_SESSION {
        int session_id PK
        int user_id FK
        string detected_intent
        string language
    }
    BENEFICIARY {
        int beneficiary_id PK
        int account_id FK
        string recipient_name
        string qr_reference
    }
```

| Module | Stores |
|---|---|
| 👤 **User** | Personal details, preferred language, biometric status |
| 💳 **Account** | Account info, balance, bank details |
| 💸 **Transactions** | Transfer records, payment status, transaction history |
| 🏦 **Loans** | Loan details, EMI information, loan status |
| 🎙️ **Voice Sessions** | User voice commands, detected intent, language |
| 👥 **Beneficiaries** | Trusted recipients, QR-based registrations |

---

## 🧠 AI Workflow

```mermaid
flowchart LR
    A["🗣️ User Speaks"] --> B["Whisper<br/>Speech → Text<br/><i>(infra ready, pending)</i>"]
    B --> C["Groq API<br/>Intent Detection"]
    C --> D["FastAPI<br/>Business Logic"]
    D --> E["SQLAlchemy → SQLite"]
    E --> F["gTTS<br/>Text → Speech<br/>(Hindi · Tamil · Telugu · English)"]
    F --> G["✅ User Receives Response"]
```

---

## 🛠️ Tech Stack

### Frontend

| Technology | Version | Purpose |
|---|---|---|
| React | 19.2.6 | UI framework |
| Vite | 8.0.12 | Build tool & dev server |
| React Router DOM | 7.17.0 | Client-side routing |
| Tailwind CSS | 4.3.0 | Styling framework |
| Framer Motion | 12.40.0 | Animations |
| Lucide React | 1.17.0 | Icon library |
| Axios | 1.17.0 | HTTP client |
| ESLint | 10.3.0 | Code linting |

### Backend

| Technology | Purpose |
|---|---|
| FastAPI | Async Python web framework |
| SQLAlchemy | ORM (Object-Relational Mapping) |
| SQLite | Default database (configurable via `DATABASE_URL`) |
| Python-dotenv | Environment variable management |
| CORS Middleware | Cross-Origin Resource Sharing |

### External AI/ML Services

| Service | Purpose |
|---|---|
| Groq API | LLM integration for AI banking assistant responses |
| gTTS (Google Text-to-Speech) | Audio generation in Hindi, Tamil, Telugu, English |
| Whisper | Speech-to-text — infrastructure in place, implementation pending |

---

## 🎨 User Flow

```mermaid
flowchart TD
    A["📱 Open Application"] --> B["🔒 Biometric Verification"]
    B --> C["🎤 Voice Command"]
    C --> D["🤖 AI Processing"]
    D --> E["🏦 Banking Operation"]
    E --> F["🔊 Voice Confirmation"]
```

---

## 📈 Future Enhancements

- [ ] UPI Integration
- [ ] Voice Biometrics
- [ ] Offline Speech Recognition
- [ ] AI Fraud Detection
- [ ] WhatsApp Voice Banking
- [ ] Multi-Bank Aggregation
- [ ] Regional Dialect Support

---

## ⭐ Project Vision

<div align="center">

*"Making Digital Banking Accessible Through Voice, AI, and Inclusive Design."*

</div>
