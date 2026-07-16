---
title: Record architecture decisions as ADRs
status: accepted
date_proposed: 2025-11-03
date_accepted: 2025-11-05
author: fabio
tags: [process]
affects:
  - adrs/**
---

## Context

Acme Parcel's platform decisions were living in chat threads and tribal memory.
New engineers re-litigated settled questions because nothing recorded what was
decided, by whom, or why.

## Decision

Every architecturally significant decision is recorded as an ADR in `adrs/`,
following the fuego-adr convention: numbered `*.adr.md` files with status
frontmatter and Context / Decision / Consequences sections.

## Consequences

Decisions become reviewable in pull requests and browsable as a site. The
discipline costs a little writing time per decision; in exchange, "why is it
like this?" has a permanent answer.
