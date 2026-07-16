---
title: Split the monolith into an API service and a worker
status: accepted
date_proposed: 2025-11-10
date_accepted: 2025-11-20
author: fabio
approvers: [alice, bob]
tags: [architecture]
affects:
  - services/**
---

## Context

The parcel-tracking monolith coupled webhook ingestion with customer-facing
reads. A burst of carrier webhooks would degrade the tracking API for every
customer, and the two workloads wanted different scaling profiles.

## Decision

Split into two deployables: **api** (synchronous reads, customer auth) and
**worker** (webhook ingestion, notification fan-out). They share a database
but never call each other synchronously.

## Consequences

Independent scaling and deploy cadence per workload. The shared database is an
accepted coupling until event volume justifies more (see the event-bus
proposal). Two Dockerfiles and two deployment manifests to maintain.

## Alternatives

A full microservice decomposition (per-domain services) was rejected as
premature: two engineers cannot operate eight services.
