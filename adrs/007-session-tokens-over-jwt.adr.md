---
title: Server-side session tokens replace JWTs
status: accepted
supersedes: [4]
date_proposed: 2026-02-02
date_accepted: 2026-02-10
author: bob
approvers: [fabio, alice]
tags: [security, api]
affects:
  - services/api/auth/**
---

## Context

ADR-004's stateless JWTs made revocation impossible: a leaked carrier token
stayed valid until expiry. Compliance now requires immediate revocation.

## Decision

Opaque session tokens stored server-side (Postgres-backed, cached in memory),
revocable at any moment. JWTs are retired from all auth paths.

## Consequences

Revocation is a row delete. Each request costs a token lookup — absorbed by
the read replicas. Supersedes ADR-004.
