# Pages: from Jekyll to Quartz (richer rendering)

GitHub Pages currently uses Jekyll which does not render Obsidian-style `[[wikilinks]]`. For a proper digital-garden experience, migrate to **Quartz v4**:

```bash
git clone https://github.com/jackyzha0/quartz.git
cd quartz
# Copy this repo's content into Quartz's content/ dir
# Configure quartz.config.ts
# npx quartz build
# npx quartz sync
```

Quartz handles Obsidian wikilinks, transclusion, graph view, and full-text search. Deploys via GitHub Actions to a separate branch consumed by Pages.

For now Jekyll renders the README and standard markdown links; clicking from README navigates; `[[wikilinks]]` show as raw text.
