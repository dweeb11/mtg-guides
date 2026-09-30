# mtg-guides

Verified, clickable HTML strategy guides for Magic: The Gathering — **limited and constructed**.

- **Limited:** `docs/hobbit/` — The Hobbit (HOB) draft & sealed (5 archetypes, Storied/Recruit/Hone, prerelease kit) — Aug 12 2026 verified
- **Constructed:** `docs/standard-bo1-2026-08-13/` — Standard Best-of-One meta, 8 Arena-importable decks (post-ban, S tier Mono-G/Spellementals) — Aug 13 2026 verified
- **Skill:** `skills/mtg-guide/SKILL.md` — reusable Pi/Hermes skill that built both guides (v0.2.0, not limited-specific)

## Browse — GitHub Pages

- **Landing:** [https://dweeb11.github.io/mtg-guides/](https://dweeb11.github.io/mtg-guides/) (resolves root; was 404 before `docs/index.html`)
- Hobbit guide: [https://dweeb11.github.io/mtg-guides/hobbit/](https://dweeb11.github.io/mtg-guides/hobbit/) — or [`docs/hobbit/index.html`](docs/hobbit/index.html)
- Standard BO1 report: [https://dweeb11.github.io/mtg-guides/standard-bo1-2026-08-13/](https://dweeb11.github.io/mtg-guides/standard-bo1-2026-08-13/) — or [`docs/standard-bo1-2026-08-13/index.html`](docs/standard-bo1-2026-08-13/index.html)
- Build status: `docs/hobbit/STATUS.md`, `docs/standard-bo1-2026-08-13/STATUS.md`

## Use the skill

```bash
# Pi discovers it as mtg-guide; also aliased as mtg-limited-guide (deprecated stub)
# Trigger: "build me a draft/sealed/standard BO1 guide for [set]"
```

## Sources and maintenance

The guides retain public source links, verification dates, and provisional-tier notes. Keep internal research job IDs, local paths, and account or gateway troubleshooting in an ignored `.private/` directory.

Before committing from a local clone of this repository, configure its private commit email:

```bash
git config --local user.email "80615739+dweeb11@users.noreply.github.com"
```

Repeat this once for each clone used to publish updates. Existing commit metadata is unchanged.

The **Secret scan** workflow checks current files and available Git history on pushes and pull requests using a pinned, checksum-verified Gitleaks release. Findings are redacted. This check detects problems after a push; GitHub push protection can prevent supported credentials from being pushed in the first place. Check repository **Settings → Security → Advanced Security** for secret scanning and push protection, and account **Settings → Emails** for **Keep my email addresses private** and **Block command line pushes that expose my email**.

Do not publish credentials, private keys, local backups, raw research output, or gateway/login diagnostics. `.gitignore` helps prevent accidental additions; it does not protect already tracked files or explicitly forced additions.

*Fan content, not affiliated with Wizards of the Coast.*
