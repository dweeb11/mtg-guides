---
name: mtg-guide
description: Build a verified, clickable HTML strategy guide for any Magic: The Gathering set — limited (draft/sealed/prerelease) or constructed (Standard BO1/BO3, Pioneer, Modern). Each guide wears its set's visual identity (palette/mood/motifs from official art direction); the repo landing page stays critterhaus-design. Use when user asks for "MTG draft guide", "sealed guide", "prerelease guide", "limited strategy", or names a set like "The Hobbit" or "Lorwyn Eclipsed".
version: 0.3.2
author: dweeb11
license: MIT
metadata:
  hermes:
    tags: [mtg, magic, limited, draft, sealed, prerelease]
    related_skills: []
---

# MTG Limited Guide Builder — First Pass

Reusable skill that started with the Hobbit limited build (2026-08-12) and the Standard BO1 report (2026-08-13). Produces single-file offline HTML guides in ignored `.build/<slug>/` directories + `STATUS.md` checkpoint. Supports both limited and constructed outputs in the same repo.

## When to use
- User names an MTG set + wants draft and/or sealed strategy
- User says "strategy guide", "prerelease guide", "limited guide" for any Universes Beyond or Standard set
- Re-run after 17Lands matures to upgrade provisional tiers → verified

## Workflow (do this every time)

### 1) Resolve the set
- Slug the set: `the-hobbit` → `hobbit`, `lorwyn-eclipsed` → `lorwyn-eclipsed`
- Private build directory: `.build/<slug>/` inside the repository
- If `STATUS.md` exists, read it — respect the pause/resume checkpoint.

### 2) Deep research (required — don't fake mechanics)
Run `hermes_research` tier `deep` with `auto` routing. Signals: breadth 2, browserIntensity 2, sourceDifficulty 2, synthesis 2.

**Query template:**
```
Do deep research on Magic: The Gathering — <Set Name> (code <CODE> if known). Find all available prerelease, preview season, spoiler, and early release information through today.

Needed:
- Official name, code, size (draft vs total), format legality, dates (debut, gallery, prerelease, Arena/MTGO, tabletop, Gift Bundle), products
- Confirmed mechanics with official reminder text (headline vs supporting), especially new keywords
- Real draft archetypes (HOB was 5, not 10) with signposts + hybrid commons/uncommons + typal lands
- Limited environment: speed, curve, color depth, early consensus rankings (flag provisional pre-17Lands)
- Sealed/prerelease guidance (Wizards baseline + expert synthesis)
- Bombs / premium removal / breakout commons-uncommons / tricks to play around
- Links: Wizards Mechanics/Release Notes/Prerelease/Collecting, Scryfall, MTGGoldfish, MythicSpoiler, Draftsim, LR/Lords of Limited, Reddit megathreads

Cite every product/mechanic/archetype claim with primary sources. Call out contradictions and thin samples explicitly.
Title: MTG <Set> Limited Strategy Research
```

Wait for the job — don't scaffold tiers as truth before it returns. If you must scaffold, mark tiers/mechanics as PLACEHOLDER and keep its job ID only in ignored `.private/` build notes.

### 2b) Visual identity (required — guides wear the set's style)
Run a second `hermes_research` (tier `standard`: breadth 1, browserIntensity 2, sourceDifficulty 1, synthesis 0) alongside or right after the deep strategy job. It is cheap and blocks the skin, not the content.

**Query template:**
```
Find the official visual/art style of Magic: The Gathering — <Set Name> (<CODE>, <dates>). Needed for a fan strategy guide restyle: key art description, color palette and mood, card frame treatments, set symbol, and any official style/art-direction notes from Wizards design/collecting articles. Links to official gallery, collecting page, design articles. Title: <Set> visual style.
```

Extract a skin spec, not a mood board:
- palette: 3–5 hexes sampled from key art / treatments / symbol (sourced, never invented). Note bg / panel / text / accent roles.
- mood + motifs: 2–3 visual ideas that survive as CSS (e.g. shattered-mirror dividers, school crests as glyphs, saga-chapter rules). No emoji, no stock imagery.
- display font: one Google-Fonts pairing suggestion that echoes the set (body stays a highly-legible sans/mono with offline fallback). Hobbit used Cinzel; Fracture wants its own answer.
- treatment echoes: how card frames / foils / symbols translate to CSS (borders, dividers, badges) — evocation only.

Rules:
- Never hotlink or inline official Wizards art (fan content, copyright). CSS evocation only; link out to the official gallery. Card images are the exception: link card names to their Scryfall page with hover preview via Scryfall's image CDN (small for preview, normal on demand) — see Card links below.
- Skin must keep the chrome usable: contrast for body text, printable (dark base with print-safe fallback unless the set identity is explicitly light), single-file offline.
- The repo landing page (`docs/index.html`) ALWAYS stays critterhaus-design — set skins apply to guide pages only.

### 3a) Build the verified LIMITED HTML (draft/sealed)
Single-file `index.html` (no build step, works offline, printable). Required sections (9):

1. **Overview** — verified set identity table (code, size, legality, dates), Pick-Two vs Pick-One, booster size, fixing level, speed
2. **Mechanics** — each mechanic as expandable detail with: official reminder text → limited translation → deckbuilding tip. Flag "does not return" (e.g., Ring tempts you for HOB).
3. **Archetypes** — only the real supported pairs (check Wizards prerelease guide). Each: color pips, signposts (gold/hybrid/land), plan, risk/combo note, tier tag. Include fixing callout + off-archetype disclaimer.
4. **Draft** — tabbed P1 Stay Open / P2 Commit / P3 Fix & Cut / Signals. BREAD tuned to set, curve table (Wizards suggested 1/7-8/5-6/3-4/2-3/17 lands), creature counts, Pick-Two nuance if applicable.
5. **Sealed** — Sort / Build / Mana / Sideboard tabs. Rule-of-7, bombs>synergy, 23/17 skeleton, splash math (single-pip only).
6. **Prerelease Kit** — what's in the box (check Collecting article vs prerelease guide — note discrepancies), 50-minute clock, interactive checklist that writes to localStorage.
7. **Cards & Removal** — provisional table (mark provisional until ~3-4 days post-Arena). Tiers S/A/B with source cards, removal hierarchy, tricks to play around (Settle, Adventure protection, etc.).
8. **Traps** — 5+ traps + pro tips + cheat-sheet table (mulligan, splash, stalled board, Army vs exile).
9. **Sources** — dates timeline, products list, public source links and verification date, "revisit after 17Lands matures" note.

**Chrome behavior (stable across sets) + skin (per-set, from §2b):**
- Behavior to keep: sticky topbar with set code + live status (AWAITING → VERIFIED + date); hero with set dates + 3 KPIs + path toggle (Both/Draft/Sealed dims non-path) + search (`/` focuses); left TOC with scroll spy, progress bar wired to checklist `data-prog`; search filters mechanics/arch + cards, pill filters for archetype speed; print button + Reset.
- Skin from the §2b spec: CSS variables for bg/panel/text/accents, display font, motif details (dividers, badges, title treatments). Structure and JS stay identical; only the skin changes.
- localStorage keys must be namespaced per set (e.g. `fracture-path`, `hobbit-prog`) so guides never share progress state.

**Card links (do this every time):**
- Resolve every named card via the Scryfall API (`/cards/named?exact=<name>&set=<CODE>`, headers `User-Agent` + `Accept: application/json`), falling back to `?fuzzy=` then `cards/search?q=set:<CODE> "<name>"`. MDFC/adventure halves (e.g. Peer Review) resolve to their parent card. Pace requests (~2–3/sec max) — back off on 429.
- Wrap mentions in `<a class="c" href="<scryfall_uri>" data-small data-normal>` with a single fixed `#prev` tooltip (image + name), shown near cursor on hover/focus/touch, lazy-preloaded via IntersectionObserver. Click-through opens Scryfall in a new tab.
- Save the name→uri/image map as `cardmap.json` in the build dir and note it in STATUS.md.

Write via python (the `write` tool can be flaky — prefer `python3 << 'PY'` heredoc). Verify with `wc -c` and `xdg-open` check.


### 3b) Build the verified CONSTRUCTED HTML (Standard BO1/BO3, etc.)
If user asks for metagame/constructed:

- Pull live metagame (MTGGoldfish metagame/*, MTGO Challenges, Untapped/Aetherhub if available). Record scrape date + IDs.
- Include: tier table with shares, format legality + rotation, BO1 vs BO3 notes (hand smoother, no sideboard)
- Per deck: colors, share, source link + event, game plan, good vs / bad vs, mulligan line, clean Arena `Deck` block (4 Card Name), Copy button via `navigator.clipboard.writeText`.
- Brew section for up-and-comers / HOB spice.
- Flag thin samples (e.g., 2 days post-set) as provisional.
- Same chrome as limited (topbar, hero, Copy buttons, print).

### 3c) Repo layout (not limited-specific)
Target repo is `mtg-guides` (not `mtg-limited-guides`):
```
mtg-guides/
  README.md
  docs/hobbit/index.html          # limited
  docs/standard-bo1-2026-08-13/index.html  # constructed
  skills/mtg-guide/SKILL.md      # skill
  scripts/...
```
Keep private build files in ignored `.build/<slug>/` directories; use `docs/<slug>/` for published guides.

### 3d) Publish safely
- Keep internal research job IDs, local usernames/absolute paths, raw research output, backups, and login/gateway diagnostics in an ignored `.private/` directory outside `docs/`.
- Publish only public source links, verification dates, guide content, and repository-relative paths. Review the staged diff before committing.
- Use the repository owner's GitHub `noreply` address for publishing commits. For this repository: `git config --local user.email "80615739+dweeb11@users.noreply.github.com"`.
- Run Gitleaks on current files and Git history before publishing when available; the repository's Secret scan workflow checks pushes and pull requests.

### 4) Checkpoint
Write `STATUS.md` in the guide dir:
- repository-relative published file + size
- keep local open commands and backup names in ignored `.private/` notes
- what was verified vs provisional
- public research date and source links; keep job IDs in ignored `.private/` notes
- next steps (pull 17Lands after Arena+3d, add Scryfall hovers, Pages hosting)

### 5) Tell the user where to open it
Report the published Pages URL and repository-relative HTML path. Keep machine-specific open commands in private build notes.

## Provenance — reference builds
- Fracture (2026-09-29): official-source identity and strategy research → `docs/fracture/index.html` (50,604 bytes, 10 archetypes, Empower/Heartwood/Prepare) → `docs/fracture/`. Visual-style research drove the first per-set restyle; landing page restyled to critterhaus-design separately (`e251aa4`) and stays house-styled by rule.

## Provenance — Hobbit reference build
- Scaffold: 53,269 bytes placeholder (10 fake archetypes)
- Research: deep source review — returned Aug 12, verified HOB 193/321, HOC, Standard-legal, 5 archetypes, Storied/Recruit/Hone + Adventure/Amass Goblins/Landfall
- Verified: 45,582 bytes → `docs/hobbit/index.html` + `STATUS.md`; keep backups outside `docs/`

## Common pitfalls (limited + constructed)
- Don't invent 10 archetypes — check how many Wizards actually supports (HOB was 5)
- Don't treat early Reddit 3-0s as rankings — mark provisional until 17Lands n≥5000
- Legendary artifact counts as 1 for storied-like thresholds
- Double-pip removal is not a splash
- No Commander precons is a real product signal — mention it

## Verification checklist
- [ ] public sources and research date cited in guide + STATUS.md; no internal job IDs published
- [ ] visual-identity source links cited in STATUS.md; palette hexes trace to official art/treatments, none invented
- [ ] guide wears the set skin; landing page (`docs/index.html`) untouched and still critterhaus-design
- [ ] mechanics have official reminder text + source link
- [ ] archetype count matches Wizards prerelease guide
- [ ] provisional tiers explicitly flagged with revisit date
- [ ] single file opens offline, prints cleanly, search works
- [ ] no official art hotlinked/inlined except Scryfall card previews; no emoji; localStorage keys namespaced per set
- [ ] every named card links to Scryfall with hover preview; `cardmap.json` saved + noted in STATUS.md
- [ ] STATUS.md written
