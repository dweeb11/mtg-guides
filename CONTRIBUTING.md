# Publishing updates

Notes for whoever publishes to this repo (mostly the owner).

The guides retain public source links, verification dates, and provisional-tier notes. Keep internal research job IDs, local paths, and account or gateway troubleshooting in an ignored `.private/` directory.

Before committing from a local clone of this repository, configure its private commit email:

```bash
git config --local user.email "80615739+dweeb11@users.noreply.github.com"
```

Repeat this once for each clone used to publish updates. Existing commit metadata is unchanged.

The **Secret scan** workflow checks current files and available Git history on pushes and pull requests using a pinned, checksum-verified Gitleaks release. Findings are redacted. This check detects problems after a push; GitHub push protection can prevent supported credentials from being pushed in the first place. Check repository **Settings → Security → Advanced Security** for secret scanning and push protection, and account **Settings → Emails** for **Keep my email addresses private** and **Block command line pushes that expose my email**.

Do not publish credentials, private keys, local backups, raw research output, or gateway/login diagnostics. `.gitignore` helps prevent accidental additions; it does not protect already tracked files or explicitly forced additions.

The guide-building recipe, including where private build notes go, is in [`skills/mtg-guide/SKILL.md`](skills/mtg-guide/SKILL.md).
