<div align="center">

# 🎙️ FinVoice AI

### 💳 Voice-First Banking for Inclusive Financial Access

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org)
[![Gemini](https://img.shields.io/badge/Gemini_1.5-8E75B2?style=for-the-badge&logo=google&logoColor=white)](https://ai.google.dev)

</div>

---

## 🌟 Project Overview

**FinVoice AI** is an AI-powered multilingual banking assistant designed for:

- 🌾 **Rural Users**
- 👵 **Elderly Citizens**
- 👨‍🦯 **Visually Impaired Users**
- 📖 **Low-Literacy Users**
- 📱 **First-Time Smartphone Users**

Instead of navigating complex banking applications, users can simply **speak their banking requests** in their preferred language and receive **voice-based responses**.

---

## 🎯 Problem Statement

Traditional banking applications rely heavily on:

| Barrier | Impact |
|---------|--------|
| ❌ Reading | Excludes low-literacy users |
| ❌ Typing | Difficult for elderly & visually impaired |
| ❌ Complex Navigation | Overwhelming for first-time users |
| ❌ Password Management | Security vs. accessibility trade-off |

**FinVoice AI** solves this through:

| Solution | Benefit |
|----------|---------|
| ✅ Voice Commands | Hands-free, natural interaction |
| ✅ AI Understanding | Context-aware responses |
| ✅ Biometric Authentication | Secure & effortless login |
| ✅ Multilingual Interaction | Banking in your native language |

---

## 🚀 Key Features

### 🎤 Voice Banking
- Balance Enquiry
- Fund Transfer
- Loan Status
- Transaction History
- Voice Navigation

### 🌍 Multilingual Support
- Tamil · Hindi · Telugu · English

### 🤖 AI-Powered Assistance
- Natural Language Understanding
- Intent Detection
- Context-Aware Responses
- Conversational Banking

### 🔒 Secure Authentication
- Fingerprint Verification
- Face Authentication *(Future Scope)*
- Transaction Confirmation
- Beneficiary Verification

### ♿ Accessibility Focused
- Large UI Components
- Voice Navigation
- Screen Reader Friendly
- High Contrast Support

---

## 🏗️ System Architecture

```mermaid
flowchart TD
    A["🎤 User Voice Input"] --> B["Whisper (Speech → Text)"]
    B --> C["Gemini 1.5 Flash (Intent Recognition)"]
    C --> D["FastAPI Backend"]
    D --> E["👤 Users"]
    D --> F["💳 Accounts"]
    D --> G["💸 Transactions"]
    E --> H[("🗄️ PostgreSQL")]
    F --> H
    G --> H
    H --> I["Response Generation"]
    I --> J["Google TTS (Text → Speech)"]
    J --> K["🔊 Voice Response"]

    style A fill:#4CAF50,color:#fff
    style C fill:#8E75B2,color:#fff
    style D fill:#009688,color:#fff
    style H fill:#4169E1,color:#fff
    style K fill:#4CAF50,color:#fff
```

---

## 🗄️ Database Schema (ER Diagram)

```mermaid
erDiagram
    USER ||--o{ ACCOUNT : has
    USER ||--o{ VOICE_SESSION : creates
    ACCOUNT ||--o{ TRANSACTION : records
    ACCOUNT ||--o{ LOAN : holds
    ACCOUNT ||--o{ BENEFICIARY : registers

    USER {
        int user_id PK
        string full_name
        string phone_number
        string preferred_lang
        boolean biometric_status
        datetime created_at
    }

    ACCOUNT {
        int account_id PK
        int user_id FK
        string account_number
        string account_type
        decimal balance
        string bank_name
        string ifsc_code
    }

    TRANSACTION {
        int txn_id PK
        int account_id FK
        decimal amount
        string type
        string status
        datetime time
    }

    LOAN {
        int loan_id PK
        int account_id FK
        decimal amount
        decimal emi
        string status
        int tenure
    }

    VOICE_SESSION {
        int session_id PK
        int user_id FK
        string transcript
        string language
        string detected_intent
        datetime timestamp
    }

    BENEFICIARY {
        int beneficiary_id PK
        int account_id FK
        string beneficiary_name
        string account_ref
        datetime added_on
    }
```

---

## 🧠 AI Workflow

```mermaid
flowchart LR
    A["🗣️ User Speaks"] --> B["Whisper\n(Speech → Text)"]
    B --> C["Gemini\n(Intent Detection)"]
    C --> D["FastAPI\n(Business Logic)"]
    D --> E[("PostgreSQL")]
    E --> F["Google TTS\n(Text → Speech)"]
    F --> G["🔊 User Receives\nResponse"]

    style A fill:#4CAF50,color:#fff
    style C fill:#8E75B2,color:#fff
    style D fill:#009688,color:#fff
    style E fill:#4169E1,color:#fff
    style G fill:#4CAF50,color:#fff
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Frontend** | React.js | User Interface |
| **Styling** | Tailwind CSS | Responsive Design |
| **Backend** | FastAPI | API & Business Logic |
| **Database** | PostgreSQL | Data Persistence |
| **AI Model** | Gemini 1.5 Flash | Intent Recognition |
| **Speech Recognition** | Whisper | Speech-to-Text |
| **Text-to-Speech** | Google TTS | Voice Responses |
| **Authentication** | Biometric Verification | Secure Access |

---

## 🎨 User Flow

```mermaid
flowchart TD
    A["📱 Open Application"] --> B["🔐 Biometric Verification"]
    B --> C["🎤 Voice Command"]
    C --> D["🤖 AI Processing"]
    D --> E["🏦 Banking Operation"]
    E --> F["🔊 Voice Confirmation"]

    style A fill:#1a1a2e,color:#fff
    style B fill:#16213e,color:#fff
    style C fill:#0f3460,color:#fff
    style D fill:#533483,color:#fff
    style E fill:#e94560,color:#fff
    style F fill:#4CAF50,color:#fff
```

---

## 📈 Future Enhancements

| Enhancement | Description |
|-------------|-------------|
| 💸 UPI Integration | Direct UPI payment support |
| 🎙️ Voice Biometrics | Voice-based user authentication |
| 📴 Offline Speech Recognition | Banking without internet |
| 🛡️ AI Fraud Detection | Real-time anomaly detection |
| 💬 WhatsApp Voice Banking | Banking via WhatsApp voice notes |
| 🏦 Multi-Bank Aggregation | Single interface for all bank accounts |
| 🗣️ Regional Dialect Support | Hyper-local language variants |

---

<div align="center">

## ⭐ Project Vision

> *"Making Digital Banking Accessible Through Voice, AI, and Inclusive Design."*

---

Made with ❤️ for inclusive finance

</div>
