# HIPAA-Compliant Autonomous Browser for PHI

`hip-auto` defines a secure baseline for an autonomous browser that can operate on Protected Health Information (PHI) while aligning to HIPAA safeguards.

## Goals

- Handle PHI in browser automation flows with minimum necessary access.
- Protect PHI in transit, at rest, and in logs.
- Provide auditable, policy-driven autonomous behavior.

## Core Requirements

### 1) PHI Data Protection

- Encrypt PHI in transit using TLS 1.2+.
- Encrypt PHI at rest with managed key rotation.
- Redact PHI from logs, traces, screenshots, and error outputs by default.
- Prevent PHI persistence in local temp/session storage unless explicitly approved.

### 2) Access Control

- Enforce role-based access control (RBAC) and least privilege.
- Require strong authentication (SSO/MFA where available).
- Support short-lived, scoped credentials for autonomous tasks.
- Isolate tenant/workspace data boundaries.

### 3) Autonomous Agent Safety

- Restrict navigation and form submission to approved allowlists.
- Require policy checks before extraction, submission, or external transmission.
- Block unsafe actions by default and require explicit operator approval for exceptions.
- Provide deterministic action logs (who/what/when/why).

### 4) Auditing & Compliance

- Maintain immutable audit trails for PHI access and autonomous actions.
- Retain logs according to compliance policy with tamper evidence.
- Support incident response workflows and access reviews.
- Enable periodic control validation and risk assessments.

### 5) Secure Operations

- Run in hardened, sandboxed execution environments.
- Apply dependency and vulnerability scanning in CI.
- Use secrets management (never hardcode credentials).
- Define backup, disaster recovery, and breach notification procedures.

## Non-Functional Expectations

- Privacy-by-default configuration.
- Configurable policy engine for organization-specific controls.
- High availability and graceful failure behavior.
- Clear operator observability without exposing PHI.

## Acceptance Criteria

- No PHI appears in default logs or screenshots.
- All PHI reads/writes are auditable and attributable.
- Agent actions outside approved policy are blocked.
- Security and compliance controls are testable and repeatable.
