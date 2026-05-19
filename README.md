# Pokémon Emerald Seaglass — Companion Guide

A single-page web companion guide for the **Pokémon Emerald Seaglass** ROM hack. Browse the full Hoenn-ordered Pokédex, look up wild encounter locations, check legendary quest steps, mystery-gift cheat codes, and minigame rules — all in one offline-capable page.

Install it to your phone's home screen and it behaves like a native app.

## Live site

👉 **https://<your-username>.github.io/<repo-name>/**

*(Update this URL once GitHub Pages is enabled in your repo settings.)*

## Features

- **Hoenn Pokédex** (437 entries) — starting at Treecko #001, including all Gen 1–3 Pokémon retained in the hack, cross-gen evolutions through Gen 9, the 16 Alolan forms, and 8 hidden easter-egg Pokémon (Spiky-Ear Pichu, Tinkatink line, Applin line). Types reflect Seaglass's modified typing.
- **Clickable location bubbles** — every Pokémon's location list splits into individual bubbles. Click "Safari Zone SE" on Treecko's card and the page jumps straight to that region in the Encounters tab and expands it.
- **Encounters tab** — 141 locations grouped by area, with each Pokémon's types shown inline. Search by location or Pokémon name; expand/collapse all with one button.
- **Legendaries tab** — 21 legendaries grouped by acquisition method (Story / Standard regis / Mossdeep Sailor tickets / late-game sailor quests / special events), each with exact unlock conditions.
- **Items tab** — evolution stones, every evolution-trigger item (King's Rock, Black Augurite for Kleavor, the apple items, etc.), and key items with their hack-specific locations.
- **Cheats tab** — all 30 GameCube codes including the 18 monotype-run codes and easter-egg unlocks.
- **Minigames tab** — Scuba Safari rules and scoring, both Game Corner pinball boards, Wishing Well, Contests (moved to Verdanturf), DexNav, Talrega Lottery.
- **Features tab** — gameplay changes, mechanic tweaks, and a known-issues list.
- **Caught tracking** — tap the checkmark on any Pokémon to mark it caught. Progress saves automatically in your browser (localStorage) and syncs across the Pokédex and Encounters tabs.
- **Mobile-friendly** — responsive layout, install as a PWA for full-screen offline use.

## Install on iOS / Android home screen

**iPhone (Safari):** Tap the Share button → *Add to Home Screen*. The icon will appear with the Seaglass starters and "Seaglass" as the label. Launching it opens the guide full-screen with no browser chrome.

**Android (Chrome):** Tap the ⋮ menu → *Install app* (or *Add to Home screen*).

## Project structure

```
.
├── index.html                  ← the entire guide, single file
├── manifest.webmanifest        ← PWA manifest (icons, theme, display mode)
├── icons/                      ← home-screen + favicon assets
│   ├── apple-touch-icon.png
│   ├── icon-180.png
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── favicon-16.png
│   ├── favicon-32.png
│   └── favicon.ico
└── README.md
```

`index.html` is intentionally self-contained — no build step, no external JS frameworks. All data lives in JavaScript arrays near the top of the `<script>` block (`POKEMON`, `ENCOUNTERS`, `LEGENDARIES`, `ITEMS`, `CHEATS`, `MINIGAMES`, `FEATURES`). Pokémon sprites are pulled from [PokeAPI](https://github.com/PokeAPI/sprites). Custom sprite overrides can be added to the `SEAGLASS_SPRITES` object inside the script.

## Running locally

Just open `index.html` in any modern browser — that's it. No server needed for browsing.

For testing the PWA install / home-screen behaviour you do need a real server because iOS won't honour the manifest from `file://`. The simplest option:

```bash
# Python 3 (built-in, no install)
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Deploying to GitHub Pages

1. Push the repo to GitHub.
2. Go to **Settings → Pages**.
3. Set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Save. After ~30 seconds your guide is live at `https://<your-username>.github.io/<repo-name>/`.

If you set up a custom domain, no paths in this project need to change — everything is relative.

## Known limitations

- **Encounter levels / rates aren't included.** The source documentation only lists *where* each Pokémon can be found, not slot-level rates or encounter percentages. Use the in-game **DexNav** for live rate info.
- **Some auto-parsed locations** may have minor OCR artefacts (e.g. a "Pyre Summit" region that's really "Mt. Pyre Summit"). The clickable bubbles in the Pokédex tab handle these aliases automatically.

## Data sources

- **Mechanics, type changes, item locations, legendary quests, cheat codes, minigame rules**: from the official Pokémon Emerald Seaglass documentation distributed by the ROM hack's developer.
- **Hoenn Pokédex ordering, per-Pokémon location lists, sprite references**: from the Pokédex listing at [mrwalkthroughs.com](https://mrwalkthroughs.com/) for Pokémon Emerald Seaglass.
- **Pokémon sprites**: [PokeAPI/sprites](https://github.com/PokeAPI/sprites) (GitHub).

## Credits

- **Pokémon Emerald Seaglass** ROM hack and all original game content — by the Seaglass development team. This guide is a fan-made reference and is not affiliated with the developers.
- Pokémon sprites courtesy of the PokeAPI contributors.
- Cover art used for the icon set is from the official Seaglass promotional material.

## Disclaimer

This is an **unofficial fan-made reference**. It is not affiliated with, endorsed by, or sponsored by Nintendo, Game Freak, The Pokémon Company, or the Pokémon Emerald Seaglass development team. *Pokémon* and all related trademarks are the property of their respective owners. This guide hosts no ROM files, patches, or copyrighted game assets beyond publicly available sprite resources.

## License

The guide's code (`index.html` and supporting files) is released under the **MIT License** — feel free to fork, adapt for other ROM hacks, or repurpose. Game content (Pokémon names, locations, mechanics) belongs to its respective rights holders.
