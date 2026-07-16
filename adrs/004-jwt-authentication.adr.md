---
title: JWT bearer tokens for API authentication
status: superseded
superseded_by: [7]
date_proposed: 2025-11-25
date_accepted: 2025-12-01
author: bob
tags: [security, api]
affects:
  - services/api/auth/**
---

## Context

The tracking API needed stateless authentication that worked for both the web
app and carrier integrations, without a session store in v1.

## Decision

Issue signed JWTs at login; verify signatures in the api service; no
server-side session state.

## Consequences

Zero-lookup verification and easy horizontal scaling — but revocation is
impossible before expiry, and long-lived carrier tokens made that painful in
practice. Replaced by server-side session tokens in ADR-007.
