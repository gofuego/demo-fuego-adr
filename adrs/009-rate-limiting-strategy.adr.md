---
title: Rate-limiting strategy for the public API
status: tbd
deadline: 2026-08-01
date_proposed: 2026-07-01
author: fabio
tags: [api, performance]
affects:
  - services/api/**
  - k8s/base/ingress.yaml
---

## Context

Carrier integrations occasionally retry-storm the tracking API. We need a
limit that protects the platform without breaking legitimate bulk lookups.

## Decision

To be decided before the 2026-08-01 carrier onboarding: token bucket at the
ingress vs. per-client quotas in the api service.

## Consequences

Until decided, a retry storm can saturate the api pods; the deadline tracks
the next carrier go-live.
