---
title: Redis response cache for tracking lookups
status: deprecated
date_proposed: 2025-12-08
date_accepted: 2025-12-15
author: alice
tags: [performance]
affects:
  - services/api/cache/**
---

## Context

Tracking pages are read-heavy and were hammering Postgres with identical
lookups during delivery peaks.

## Decision

Cache rendered tracking responses in Redis with a 30-second TTL, keyed by
shipment id.

## Consequences

Peak database load dropped 8x. Deprecated once Postgres read replicas plus
HTTP caching headers covered the same load with one less moving part; the
cache code remains but is no longer deployed.
