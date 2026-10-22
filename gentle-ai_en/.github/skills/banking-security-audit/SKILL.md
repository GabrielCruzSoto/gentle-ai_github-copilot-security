---
name: banking-security-audit
description: "Banking security standards, OWASP, PCI/PII data handling, audit trails, and zero-trust validations. Trigger: security audits, financial logic."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Banking Security Audit Skill

## When to Use

Load this skill whenever authoring or reviewing code that interacts with:
- Payment processing, financial ledgers, account balances, or transaction routing.
- User authentication, session tokens, cryptographic signatures, or authorization grants.
- Ingestion of untrusted external payloads or sensitive customer records.

## Essential Bank Compliance Invariants

1. **Precision & Money Representation**:
   - Never use floating point numbers (`float`, `double`) for monetary amounts.
   - Use integer subunits (cents, satoshis) or arbitrary-precision decimal types (`BigDecimal`, `Decimal`).
2. **Defensive Masking of Financial & Customer Data**:
   - Mask PAN (Primary Account Number): show only last 4 digits (e.g. `**** **** **** 1234`).
   - Never serialize or dump raw request bodies containing CVV, passwords, PINs, or national IDs into application logs or telemetry.
3. **Idempotency**:
   - Financial mutations (transfers, chargebacks, debits) must require an `Idempotency-Key` to protect against duplicate execution on network retry.
4. **Tamper-Evident Audit Trails**:
   - Every state change on customer assets must emit an immutable audit event recording: timestamp (UTC), operator/client identity, operation type, before/after checksum, and IP/source channel.
5. **Fail-Closed Authorization**:
   - If a permission check encounters an error, timeout, or unexpected response from an upstream identity provider, default to `DENY`.
