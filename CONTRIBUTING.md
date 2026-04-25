# Contributing

Thanks for your interest in improving these knowledge graphs.

## What we accept

- **Regulatory updates** — new dates, scheme rule changes, retired regs
- **New atomic concept notes** — keep them ~50-200 lines
- **Vendor profile updates** — accurate, vendor-neutral language
- **New use cases / processes / state machines** — follow existing template
- **Diagram fixes** — Mermaid preferred over images
- **Cross-link improvements** — broken links, missing back-links
- **Solidity snippet additions** — must be self-contained, OZ-based, comments explaining cash mgmt context

## What we don't accept

- Marketing language ("best-in-class", "leading", "world-class")
- Vendor advocacy without basis
- AI-generated boilerplate without manual review
- Personal opinions without rationale (use ADR template if argued)

## Style

- Cave-like terseness preferred. Drop articles, drop hedging.
- Technical terms exact.
- Mermaid diagrams over ASCII art.
- Code blocks with comments for the *why*, not the *what*.
- Wiki-links `[[note-name]]` only — Obsidian-compatible.
- Headers: H1 for title, H2 for section, deeper sparingly.

## Add a new note

1. Pick the right dir (`concepts/`, `processes/`, etc. — see README)
2. Filename: lowercase, hyphens, descriptive (`my-new-concept.md`)
3. Frontmatter optional but recommended (Obsidian-compatible YAML)
4. End with `## Linked` section + back-links to related notes
5. Add to dir's `README.md` index if exists

## ADR template

For architectural / strategic decisions, add to `decisions/`:

```markdown
# ADR NNNN — Title

**Status**: Proposed | Accepted | Superseded
**Date**: YYYY-MM-DD
**Deciders**: roles, not names

## Context
What's the situation, what's the question.

## Options
A. ...
B. ...
C. ...

## Decision
**X chosen.**

## Reasoning
Why.

## Consequences
What changes downstream.

## Linked
[[../related/...]]
```

## License

By contributing you agree to license your contribution under MIT (code) and CC-BY-SA-4.0 (docs).

## Pull request checklist

- [ ] Files in correct dir
- [ ] Cross-links present and tested (no broken `[[...]]`)
- [ ] Mermaid diagrams render
- [ ] Solidity snippets compile (`forge build`)
- [ ] No personal data, no internal-only references
- [ ] No marketing language
