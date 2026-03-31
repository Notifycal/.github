
**Notifycal** is a SaaS platform that helps appointment-based businesses reduce no-shows through automated SMS reminders — synced directly with the calendar tools they already use.

## The Problem

Small and medium-sized businesses that rely on appointments — clinics, salons, consultants — share a common pain:

- Customers forget appointments
- No-shows directly impact revenue
- Manual reminders are time-consuming and unreliable

Existing solutions are too complex, overpriced, or not adapted to SMB workflows.

## What Notifycal Does

- **Syncs with Google Calendar** — connects to the calendar you already use
- **Sends automated SMS reminders** — before appointments, on your schedule
- **Configurable timing and messaging** — adapt to your business needs
- **Subscription + usage-based billing** — predictable costs with top-up flexibility
- **Usage visibility** — clear tracking of reminders sent and costs

> Connect your calendar → configure reminders → reduce no-shows automatically

## Business Model

Monthly subscription includes a base number of SMS reminders. Additional usage is covered via top-ups. Pricing is simple and predictable for SMBs, with internal balance tracking (in €) to handle varying SMS costs per country. Pricing configurable.

## Architecture

→ [Full System Architecture](https://app.diagrams.net/#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FNotifycal%2F.github%2Fmain%2Fstuff%2Ffull_architecture.drawio)

→ [Stripe & Billing](https://app.diagrams.net/#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FNotifycal%2F.github%2Fmain%2Fstuff%2Fstripe_architecture.drawio)

## Technology Stack

Notifycal is a modern, serverless SaaS platform built with scalability, reliability, and cost-efficiency as core principles, following a modular and event-driven architecture.

### Frontend

The platform has two complementary frontend layers — the **SaaS application** and a **static landing site** — sharing UI primitives and design decisions.

**SaaS Application** — single-page application (SPA):
- React + TypeScript · Vite · TanStack Router (file-based, type-safe) · TanStack Query
- Mantine + Tailwind CSS · Framer Motion · i18next · Axios (with interceptors)

**Static Landing** — built with Astro, optimized for performance and SEO:
- Astro (static generation) · partial hydration for interactive islands
- React components reused from the SaaS application

**Shared UI Layer** — single source of truth across both surfaces:
- Reusable React components · shared TypeScript types · shared Zod validation schemas

### Backend

Fully serverless, designed for horizontal scalability and minimal operational overhead:
- **AWS Lambda** (Node.js + TypeScript) · **API Gateway** (REST) · **DynamoDB**
- **SQS / SNS** for async processing · **Zod** for runtime validation · **OpenAPI** contract definition

Background processes (reminders, retries, notifications) are handled asynchronously through queues — decoupled and resilient by design.

### Infrastructure & DevOps

- **OpenTofu / Terraform** (via Terragrunt) · **GitHub Actions** (CI/CD) · **Cloudflare** (DNS + edge)
- **AWS X-Ray** for distributed tracing · **AWS Lambda Powertools** (Logger, Tracer, Metrics)

### Integrations

- **Vonage** — SMS delivery
- **Mailgun** — email notifications
- **Stripe** — billing and subscriptions
- **Google OAuth** — authentication

### Architecture Principles

- **Serverless-first** — automatic scaling, minimal operational overhead
- **Event-driven** — decoupled and resilient background processing
- **Type-safe end-to-end** — shared contracts across frontend and backend
- **Cost-aware** — optimized for early-stage efficiency
- **Modular & extensible** — easy to evolve and integrate new providers

## Roadmap

- [ ] AI agent for creating appointments to close the loop
- [ ] Microsoft 365 / Outlook Calendar integration
- [ ] Improved onboarding and self-serve experience
- [ ] No-show analytics and ROI reporting
- [ ] International expansion with localized pricing


## Videos

**Promo**

[![Promo Video](https://img.youtube.com/vi/0Tmioc5_YME/maxresdefault.jpg)](https://www.youtube.com/watch?v=0Tmioc5_YME)

**How It Works**

[![How It Works](https://img.youtube.com/vi/Q_Kpj5wz1o8/maxresdefault.jpg)](https://www.youtube.com/watch?v=Q_Kpj5wz1o8)

**Free Trial**

<video src="https://raw.githubusercontent.com/Notifycal/.github/main/stuff/free_trial_video__4_.mp4" controls width="100%"></video>

## Documents

| | |
|--|--|
| [Design Deck](https://raw.githubusercontent.com/Notifycal/.github/main/stuff/final-cmyk.pdf) | Print-ready design document |
| [Full Architecture](https://app.diagrams.net/#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FNotifycal%2F.github%2Fmain%2Fstuff%2Ffull_architecture.drawio) | System architecture diagram |
| [Stripe Architecture](https://app.diagrams.net/#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FNotifycal%2F.github%2Fmain%2Fstuff%2Fstripe_architecture.drawio) | Payment integration diagram |
| [Financials](https://raw.githubusercontent.com/Notifycal/.github/main/stuff/Finanzas.xlsx) | Pricing research and financial model |
| [Competitive Analysis](https://raw.githubusercontent.com/Notifycal/.github/main/stuff/Espionage%20de%20competencia.xlsx) | Competitor research and market positioning |
