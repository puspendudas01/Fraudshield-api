# Fraudshield-api
# FraudShield API   
A secure transaction monitoring REST API that detects suspicious activity using a rules-based fraud scoring engine.

---

## Overview
**FraudShield API** is a cybersecurity-focused backend service built with **FastAPI** that:
- authenticates users using **JWT**
- accepts transaction requests
- assigns a **fraud risk score (0–100)**
- classifies transactions as **ALLOW / FLAG / BLOCK**
- logs security events for monitoring and auditability

This project simulates real-world fraud prevention systems used in fintech and audit/security domains.

---

## Key Features

### Authentication & Access Control
- JWT-based authentication (Register / Login / Protected routes)
- Password hashing (bcrypt)
- Role-based access control (**admin/user**)

### Fraud Detection (Rules-Based Engine)
- Fraud scoring using multiple security rules:
  - high transaction amount
  - odd-hour transactions
  - new device detection
  - burst transactions in short time window
  - risky merchants list
- Decision output: **ALLOW / FLAG / BLOCK**
- Stores risk score + triggered rules for each transaction

### Security Audit Logging
- Tracks sensitive events such as:
  - login success/failure
  - flagged/blocked transactions
  - admin access to security logs
- Stores IP address, user-agent and details for traceability

---

## Tech Stack
- **FastAPI** (Python)
- **SQLite** (Database)
- **SQLAlchemy** (ORM)
- **JWT Authentication**
- **Docker**
- **GitHub Actions** (CI)

---

## API Endpoints

### Auth
- `POST /auth/register`
- `POST /auth/login`
- `GET /auth/me`

### Transactions
- `POST /tx` → create transaction + fraud score
- `GET /tx/me` → list my transactions

### Risk
- `GET /risk/me` → show only flagged/blocked transactions

### Admin
- `GET /admin/risk/overview`
- `GET /admin/security/logs`
