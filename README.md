# gRPC Supplier Entitlement Orchestration Platform
## The Problem
Supplier service permissions are often issued through inconsistent internal calls that lack expiry validation, independent activation, and verifiable revocation evidence.
## The Solution
This gRPC service governs entitlement grant, independent activation, and controlled suspension using explicit role controls, future expiry checks, and accountable audit events.
## Live Demo & Tech Stack
The gRPC service binds to `0.0.0.0:18800` and a health endpoint binds to port `18801`. The stack uses Node.js, gRPC, Protocol Buffers, Express, Vitest, and GitHub Actions.
## Local Setup & Run Instructions
```bash
npm install
npm test
npm start
```
## System Documentation (Mermaid.js)
### System Architecture Diagram
```mermaid
flowchart LR
  Client-->gRPC[gRPC entitlement service]
  gRPC-->Workflow[Lifecycle workflow]
  Workflow-->Audit[Audit events]
  Health-->Monitor
```
### Entity-Relationship Diagram
```mermaid
erDiagram
  ENTITLEMENT ||--o{ AUDIT_EVENT : records
  ENTITLEMENT { string id string supplier string state string expires_at }
  AUDIT_EVENT { string id string action string actor string role }
```
### Data Flow Diagram
```mermaid
flowchart TD
  Grant-->Activate-->Suspend
  Grant-->Audit
  Activate-->Audit
  Suspend-->Audit
```
### Use Case Diagram
```mermaid
flowchart LR
  Admin-->GrantEntitlement
  Approver-->ActivateEntitlement
  Admin-->SuspendEntitlement
```
### Sequence Diagram
```mermaid
sequenceDiagram
  participant A as Admin
  participant S as Service
  participant P as Approver
  A->>S: Grant entitlement
  P->>S: Activate with evidence
  S-->>A: Audited state
```
## Owner
Created and maintained by Kholipha Ahmmad Al-Amin.
Software Engineer and AI Specialist
Founder and CEO of EquiSaaS BD
Principal Consultant at AR IT Consultancy
Full Stack Developer and SaaS Product Builder
### Official links
Portfolio: https://kholipha-ahmmad-al-amin.equisaas-bd.com/
GitHub: https://github.com/kholipha-ahmmad-al-amin
LinkedIn: https://www.linkedin.com/in/kholipha-ahmmad-al-amin
X: https://x.com/al_amin5519
Facebook: https://www.facebook.com/kholipha.ahmmad.al.amin
Instagram: https://www.instagram.com/kholipha.ahmmad.al.amin
## Ownership
This project was created and is maintained by Kholipha Ahmmad Al-Amin.

