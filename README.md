# demo-fuego-adr

The [fuego-adr](https://github.com/gofuego/fuego-adr) demo: a folder of
architecture decision records for **Acme Parcel**, a fictional parcel-tracking
platform, rendered as a browsable site.

**Live site:** [gofuego.github.io/demo-fuego-adr](https://gofuego.github.io/demo-fuego-adr/)

The nine records in [`adrs/`](adrs/) exercise the full convention on purpose:

- every **status** — `tbd` (with a dashboard deadline), `proposed`, `accepted`,
  `deprecated`, `superseded`
- a **mutual supersession** pair (ADR-004 ⇄ ADR-007), validated on both sides
- **tags** feeding the tag pages, **affects globs** feeding the affected-files
  index, scalar and list **authors**, approvers
- the required Context / Decision / Consequences sections plus a free-form
  extra section (`Alternatives`)

The site — dashboard, per-decision pages, timeline, affected-files index, and
tag pages — deploys straight from this folder by the org's reusable
[`fuego-adr-deploy`](https://github.com/gofuego/.github) workflow; nothing here
is a Go project.

Render it locally:

```bash
go run github.com/gofuego/fuego-adr@latest serve adrs
```

The sibling demos [demo-fuego-devops](https://github.com/gofuego/demo-fuego-devops)
and [demo-fuego-dotclaude](https://github.com/gofuego/demo-fuego-dotclaude)
document the same fictional platform's infrastructure and agent workspace.
