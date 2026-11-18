# WPMS-LEO
### Washing Plant Management System

**A full-stack manufacturing operations management application built with React, TypeScript, Flask, and MySQL.**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white) ![React](https://img.shields.io/badge/React-149ECA?style=flat-square&logo=react&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)

**Status:** Active Development | **Architecture:** Full-Stack Web Application

---

## Overview

WPMS-LEO is a web-based management system designed to digitize and streamline operational workflows in an industrial garment washing and finishing facility.

The project aims to replace fragmented manual records with a centralized system connecting customer management, goods receiving, production operations, chemical inventory, dispatch, invoicing, and payment tracking.

It emphasizes **data integrity, traceability, role-based security, and reliable business transaction processing**.

## The Problem

Industrial washing facilities handle garments from multiple customers, often involving different garment styles, washing processes, production batches, and delivery schedules.

Traditional manual or spreadsheet-based workflows can make it difficult to:

- Track garments received, processed, and dispatched.
- Manage partial deliveries across multiple receiving records.
- Maintain accurate chemical inventory.
- Monitor production activities and equipment.
- Generate accurate customer invoices.
- Prevent duplicate billing.
- Track outstanding customer payments.
- Maintain accountability for operational changes.

WPMS-LEO addresses these challenges through an integrated, database-driven application.

## System Architecture

```text
                 ┌────────────────────────┐
                 │       React UI         │
                 │   TypeScript + Vite    │
                 └────────────┬───────────┘
                              │
                         REST API
                              │
                 ┌────────────▼───────────┐
                 │     Flask Backend      │
                 │                        │
                 │  Routes / Controllers  │
                 │  Business Services     │
                 │  Authentication & RBAC │
                 │  Validation & Auditing │
                 └────────────┬───────────┘
                              │
                         SQLAlchemy
                              │
                 ┌────────────▼───────────┐
                 │      MySQL Database    │
                 │                        │
                 │  Relational Data       │
                 │  Transaction Records   │
                 │  Constraints & Indexes │
                 └────────────────────────┘
```

The backend follows a layered architecture that separates API routing, business logic, and persistence.

Database schema changes are version-controlled using Alembic migrations.

## Core Modules

| Module | Description | Status |
|---|---|---|
| Authentication & RBAC | Secure login, permissions, and session management | Implemented |
| User Administration | Employee accounts, roles, password resets, and account management | Implemented |
| Master Data | Customers, vendors, garment styles, processes, chemicals, and equipment | Foundation implemented |
| Goods Receiving | Multi-line garment receiving records and quantity tracking | Planned |
| Production Management | Washing processes, production batches, and machine allocation | Planned |
| Chemical Inventory | Lot-level stock, consumption, and inventory movements | Planned |
| Dispatch Management | Partial deliveries and receiving-record allocations | Planned |
| Customer Invoicing | Delivery-based, process-wise billing | Planned |
| Payment Management | Partial payments and outstanding balances | Planned |
| Reporting & Analytics | Operational and financial dashboards | Planned |

Module status will be updated as development progresses.

## Authentication & Security

WPMS-LEO incorporates a role-based authentication and authorization system.

Key capabilities include:

- Session-based authentication using Flask-Login.
- Role-based access control (RBAC).
- Backend-enforced permissions.
- Administrator-controlled employee management.
- Password hashing and password policy validation.
- Mandatory password changes for temporary credentials.
- Account activation and deactivation.
- CSRF protection and session security controls.
- Audit logging for sensitive operations.
- Protection against removing the last active administrator.

The system separates frontend navigation permissions from backend authorization to ensure restricted API endpoints remain protected independently of the user interface.

## Operational Workflow

The planned end-to-end workflow is:

```text
Customer & Style Registration
             │
             ▼
       Goods Receiving
             │
             ▼
      Production Planning
             │
             ▼
     Washing & Finishing
             │
             ▼
       Quality Control
             │
             ▼
       Goods Dispatch
             │
             ▼
      Monthly Invoicing
             │
             ▼
      Payment Tracking
             │
             ▼
    Reports & Analytics
```

### Quantity Traceability

A central design requirement is the ability to track garment quantities across multiple receiving and dispatch records.

For example, a customer may deliver 1,000 garments under one receiving record, while the factory dispatches 400 garments initially and the remaining 600 later.

The system is designed to maintain line-level allocations so that received, dispatched, and remaining quantities can be reconciled.

### Delivery-Based Billing

The proposed billing architecture supports charging customers for completed washing and finishing processes only after the corresponding garments have been dispatched.

Invoice allocation records will link billed quantities to delivered garments, supporting partial invoicing and preventing duplicate billing.

These operational and billing workflows are part of the planned implementation.

## Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite |
| Backend | Python, Flask |
| ORM | SQLAlchemy |
| Database | MySQL |
| Migrations | Alembic |
| Authentication | Flask-Login |
| API Architecture | REST |
| Testing | Python backend tests and browser-based verification |
| Version Control | Git, GitHub |

## Project Structure

```text
WPMS-LEO/
├── backend/
│   ├── app/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   └── utils/
│   ├── migrations/
│   ├── tests/
│   └── requirements.txt
│
├── frontend/
│   └── src/
│       ├── components/
│       ├── pages/
│       └── services/
│
├── docs/
├── .gitignore
└── README.md
```

*The directory structure may evolve as additional modules are implemented.*

## Engineering Principles

**Layered architecture:** Separation of presentation, API, business logic, and data persistence.

**Database integrity:** Foreign keys, constraints, transactions, and version-controlled schema migrations.

**Security by design:** Role-based permissions, password protection, authenticated sessions, and auditability.

**Traceability:** Linking operational records across goods receiving, production, dispatch, and billing.

**Modularity:** Independent business modules built on shared master data and reusable services.

**Testing:** Automated regression tests and manual verification of critical workflows.

## Development Roadmap

- [x] Backend architecture and database foundation
- [x] Authentication and role-based authorization
- [x] Administrator user management
- [x] Initial master-data implementation
- [ ] Authentication finalization and security regression testing
- [ ] Goods Receiving Note (GRN) management
- [ ] Garment inventory and quantity reconciliation
- [ ] Production and washing process tracking
- [ ] Dispatch management
- [ ] Customer invoicing
- [ ] Payment and outstanding balance management
- [ ] Operational dashboards and reporting
- [ ] Windows local deployment

## Screenshots

Application screenshots will be added as the user interface evolves.

Screenshots and demonstrations will use fictional data to protect business and customer information.

## Development & Deployment

The application is being developed in a local environment, with a planned single-machine Windows deployment.

Public setup instructions and sanitized example configuration will be added after the repository structure and environment requirements are finalized.

Real database credentials, environment files, backups, and operational data are not intended to be included in this repository.

## Project Focus

WPMS-LEO demonstrates practical application of:

- Full-stack software engineering
- REST API development
- Relational database modeling
- Authentication and authorization
- Transaction-oriented business logic
- Operational workflow design
- Software testing and maintainability

The project is under active development, with an emphasis on building a reliable operational foundation before introducing advanced analytics.

---

**WPMS-LEO | Industrial Operations • Full-Stack Engineering • Data Integrity**
