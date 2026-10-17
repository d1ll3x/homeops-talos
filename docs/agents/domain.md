# Domain Docs

How the engineering skills should consume this repo's domain documentation when exploring the codebase.

## Before exploring, read these

- **`GLOSSARY.md`** at the repo root.
- **ADRs** in the Obsidian vault at `~/Documents/zettelkasten/200-projects/talos/adr/`: read ADRs that touch the area you're about to work in. ADRs are deliberately kept out of the repo.

If any of these don't exist, **proceed silently**. Don't flag their absence; don't suggest creating them upfront. The `/domain-modeling` skill (reached via `/grill-with-docs` and `/improve-codebase-architecture`) creates them lazily when terms or decisions actually get resolved.

## File structure

Single-context, split between repo and vault:

```
~/repos/homeops-talos/
├── GLOSSARY.md
└── talos/

~/Documents/zettelkasten/200-projects/talos/adr/
├── adr-0001-<kebab-title>.md
└── adr-0002-<kebab-title>.md
```

## Writing ADRs

- Before creating or editing an ADR, read `~/.claude/docs/vault-notes.md` and follow its frontmatter template and timestamp rules (tag `projects/talos`).
- Filename: `adr-NNNN-<kebab-title>.md`, numbered sequentially.
- The vault gets reorganised. If the `adr/` folder isn't where expected, search the whole vault (`rg -l 'adr-0' ~/Documents/zettelkasten`) before creating a new one.
- Never git-commit the vault.

## Use the glossary's vocabulary

When your output names a domain concept (in an issue title, a refactor proposal, a hypothesis, a test name), use the term as defined in `GLOSSARY.md`. Don't drift to synonyms the glossary explicitly avoids.

If the concept you need isn't in the glossary yet, that's a signal: either you're inventing language the project doesn't use (reconsider) or there's a real gap (note it for `/domain-modeling`).

## Flag ADR conflicts

If your output contradicts an existing ADR, surface it explicitly rather than silently overriding:

> _Contradicts ADR-0007 (event-sourced orders), but worth reopening because…_
