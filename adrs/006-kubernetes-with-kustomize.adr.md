---
title: Deploy on Kubernetes with Kustomize overlays
status: accepted
date_proposed: 2026-01-07
date_accepted: 2026-01-14
author: [fabio, bob]
approvers: [alice]
tags: [infrastructure, deployment]
affects:
  - k8s/**
  - services/*/Dockerfile
---

## Context

Staging and production drifted apart when manifests were copy-pasted per
environment. We needed one source of truth with per-environment variance
expressed, not duplicated.

## Decision

Kubernetes for orchestration; manifests as a Kustomize **base** plus
`staging` and `production` overlays. Overlays patch replicas, resources, and
environment config only.

## Consequences

Environment diffs are reviewable patches instead of parallel files. Everyone
edits the base; the overlays stay thin. Local tooling needs `kustomize` to
render what the cluster actually applies.
