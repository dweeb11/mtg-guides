# mtg-guides

Clickable, printable strategy guides for Magic: The Gathering sets, researched and built by an AI agent.

I love playing Magic. As an experiment, I wanted to see whether an AI agent could be my set tutor: research a new set from real sources and turn it into the guide I'd want at the table. These are the results, plus the recipe it follows.

**→ [dweeb11.github.io/mtg-guides](https://dweeb11.github.io/mtg-guides/)**

| Guide | Format | As of |
|---|---|---|
| [Reality Fracture](https://dweeb11.github.io/mtg-guides/fracture/) | Draft & Sealed | Sep 29, 2026 · updated Oct 7 with win rates |
| [Standard Best-of-One](https://dweeb11.github.io/mtg-guides/standard-bo1-2026-10-07/) | Constructed | Oct 7, 2026 |
| [The Hobbit](https://dweeb11.github.io/mtg-guides/hobbit/) | Draft & Sealed | Aug 12, 2026 · archive |
| [Standard Best-of-One, August](https://dweeb11.github.io/mtg-guides/standard-bo1-2026-08-13/) | Constructed | Aug 13, 2026 · archive |

Each guide is a single HTML page: nothing to install, works offline, prints to PDF. Card names link to Scryfall with hover previews. Launch-week tier rankings are marked provisional until real win-rate data exists, then re-graded against it.

## How they're made

An agent researches each set from Wizards' mechanics articles, release notes, and prerelease guide, plus community reviews (Draftsim, Limited Resources, Lords of Limited, 17Lands). It quotes mechanics from official reminder text, checks the archetype count against Wizards' own list, styles the page after the set's official art direction, and flags anything still unproven. Every guide lists its sources.

The full recipe is [`skills/mtg-guide/SKILL.md`](skills/mtg-guide/SKILL.md). Treat it as a reference, not a plug-and-play tool: it relies on the author's own research tooling and house style.

## License

The skill and page code are [MIT](LICENSE). The guide writing is [CC BY 4.0](LICENSE-CONTENT): share and adapt it with credit. Neither covers Wizards of the Coast material.

---

Unofficial Fan Content permitted under the [Fan Content Policy](https://company.wizards.com/en/legal/fancontentpolicy). Not approved/endorsed by Wizards. Portions of the materials used are property of Wizards of the Coast. ©Wizards of the Coast LLC.
