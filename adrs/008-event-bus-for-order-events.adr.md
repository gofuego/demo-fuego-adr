---
title: Event bus between api and worker
status: proposed
date_proposed: 2026-06-20
author: alice
tags: [architecture, messaging]
affects:
  - services/worker/**
  - services/api/events/**
---

## Context

The api and worker currently coordinate through the shared database (ADR-002's
accepted coupling). Webhook volume has tripled; polling the events table is
the top query by load.

## Decision

Introduce a lightweight event bus (NATS) carrying shipment events; the worker
consumes instead of polling. The shared database remains the system of record.

## Consequences

Decouples write bursts from read load and removes the hottest query. Adds an
operational dependency that must be deployed, monitored, and drained on
upgrade.
