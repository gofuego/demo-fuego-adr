---
title: PostgreSQL for persistence
status: accepted
date_proposed: 2025-11-12
date_accepted: 2025-11-18
author: alice
approvers: [fabio]
tags: [database, infrastructure]
affects:
  - services/api/store/**
  - k8s/base/postgres.yaml
---

## Context

Parcel events are relational (shipments, scans, notifications) and the team
knows SQL. The choice was between PostgreSQL, MySQL, and a hosted document
store.

## Decision

PostgreSQL 16, self-hosted in the cluster for staging and managed in
production. Schema migrations ship with the api service.

## Consequences

One battle-tested store, JSONB where flexibility is needed. Running stateful
Postgres in staging means the cluster needs a PVC story; production offloads
that to the managed offering.
