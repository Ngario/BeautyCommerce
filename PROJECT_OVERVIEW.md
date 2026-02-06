# Beauty E-Commerce Platform — Project Overview

## What This Project Is

This repository is the **Beauty E-Commerce Platform**: a full-stack web application for selling beauty products online in **Kenya**. Customers can browse products, add them to a cart, and pay using **M-Pesa** (via Daraja API) or **bank/card payments** (via Pesapal). The system is built to be **secure**, **scalable**, and **maintainable**, with a clear split between frontend, backend, and database.

---

## Why This Stack

| Layer | Choice | Reason |
|-------|--------|--------|
| **Frontend** | React + TypeScript + Vite | Fast development, type safety, and a modern build pipeline. |
| **Styling** | Tailwind CSS | Responsive, mobile-first UI with minimal custom CSS. |
| **Backend** | Node.js + NestJS | TypeScript-first, structured modules, built-in support for auth, validation, and APIs. |
| **Database** | PostgreSQL + Prisma | Reliable relational data, type-safe queries, and clear schema. |
| **Payments** | M-Pesa Daraja + Pesapal | Matches how customers in Kenya actually pay (mobile money and banks). |
| **Files** | Cloudinary | Product images stored and delivered via CDN. |
| **Deployment** | Docker + Render | Same environment locally and in production; easy to scale. |

---

## High-Level Architecture

```
┌─────────────────┐     HTTPS      ┌─────────────────┐     ┌─────────────────┐
│   Frontend      │ ◄────────────► │   Backend       │ ◄──► │   PostgreSQL    │
│   (React/Vite)  │   REST/GraphQL │   (NestJS)      │     │   (Prisma)      │
└─────────────────┘                └────────┬────────┘     └─────────────────┘
        │                                  │
        │                                  ├──► M-Pesa Daraja API
        │                                  ├──► Pesapal API
        │                                  └──► Cloudinary
        │
        └── Static build deployed on Render (e.g. static site)
```

- **Frontend**: Lives in the `frontend` folder. Talks to the backend over HTTPS only.
- **Backend**: Lives in the `backend` folder. Handles users, products, orders, payments, and file uploads.
- **Database**: PostgreSQL; schema and access are defined and managed via Prisma in the backend.

---

## Main Features (Scope)

### Customer-Facing (Frontend)

- Product listing with filters (category, price, brand, stock).
- Product detail pages (images, description, variants).
- Shopping cart and checkout.
- User sign-up, login, and password recovery.
- Order history and account management.
- Forms validated with React Hook Form + Zod; auth via JWT or secure cookies.

### Backend

- REST or GraphQL APIs for products, users, orders, and payments.
- JWT authentication and role-based access.
- Order lifecycle: create, update, track.
- M-Pesa STK Push (Daraja) with callbacks and verification.
- Pesapal integration for bank/card payments and confirmation callbacks.
- Product image uploads to Cloudinary.
- Centralized errors, logging, and validation (e.g. class-validator).
- Transactions (e.g. Prisma `$transaction`) for payments and stock updates.

### Data (Database)

- PostgreSQL with Prisma models for: **Users**, **Products**, **Orders**, **Payments**, **Categories**, **Inventory**, and proper relationships and constraints.

### Infrastructure

- Docker for frontend and backend (and optionally DB) for consistent environments.
- Deployment on Render: backend as a web service, frontend as a static site, PostgreSQL as a managed database.
- Configuration via environment variables; HTTPS enforced.

---

## Repo Structure (Planned)

```
BeautyCommerce/
├── frontend/          # React + TypeScript + Vite + Tailwind
├── backend/           # NestJS + Prisma
├── PROJECT_OVERVIEW.md   # This file
└── (project rules and docs as we add them)
```

You have already created the `backend` and `frontend` folders; we will fill them step by step with a clear, split architecture.

---

## How We Will Proceed

1. **Step-by-step and sequential** — Each part (e.g. backend setup, auth, payments) will be introduced in order, with short explanations so you can master the concepts.
2. **Documentation** — Decisions, errors, and fixes will be documented so we don’t repeat mistakes and the design stays clear.
3. **Permission before code** — No code tasks will be executed without your explicit permission.
4. **Rules in .md files** — Project rules (errors log, code splitting, architecture, when to advise, and permission-based workflow) will be captured in dedicated .md files and followed throughout.

---

## Next Steps (After Your Permission)

Once you confirm, we will:

1. Add **project rules** in .md files (error log, code-splitting/architecture, “big picture” and deployment, when to advise, and “ask before code”).
2. Then proceed in sequence: e.g. backend foundation (NestJS + Prisma + Docker), then auth, then products, then orders and payments (M-Pesa + Pesapal), then frontend, then deployment.

**No further code or structure changes will be made until you give permission to continue.**
