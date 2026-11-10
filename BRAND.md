# Plasmid brand rules

Draft 1 · 2026-11-10 · owner: DNAngeluS

Plasmid is the part of DNAngeluS that lives inside other people's engines. This file defines how it is named, how it sounds, how the mark is built, and how the design system extends the one at [dnangelus.ar](https://dnangelus.ar). The visual reference for everything below is `brand/construction-sheet.png`; `brand/mark-draft.svg` is the mark itself and `brand/tokens.css` holds the tokens.

## 1. Concept

A plasmid is a small ring of DNA that lives beside a cell's genome, carries a few genes, and is copied between cells intact. That is the toolkit.

| Biology | Plasmid Labs |
|---|---|
| genome | **DNAngeluS**. The identity everything comes from. |
| host cell | **CRYENGINE**. Never modified. |
| plasmid | **The toolkit.** Small, self-contained, portable. |
| gene | **One tool**: dev, assets, debug, mcp. |
| insertion site | Where a tool plugs in: a CMake fragment, a console command, a pinned copy. |
| uptake | Vendoring a tagged copy into a project. The copy is never edited. |
| marker gene | Health checks. Proof the insert took (`make health`). |

Brand architecture, three tiers:

```
DNAngeluS          genome   personal brand, every project originates here
 └─ Plasmid Labs   lab      the org: github.com/plasmid-labs
     └─ plasmid    ring     the family and the root repo
         ├─ plasmid-dev
         ├─ plasmid-assets
         ├─ plasmid-debug
         └─ plasmid-mcp
```

Plasmid is DNAngeluS, a personal brand. It carries no Khem Labs marks and Khem Labs carries none of Plasmid's.

## 2. Naming

1. Family names are `plasmid-<noun>`: lowercase, one hyphen, one short English noun for the job the tool does. The pun stops at the first word. `plasmid-debug`, not `plasmid-mutagen`.
2. The noun list is closed for now: `dev`, `assets`, `debug`, `mcp`. A new tool gets a new noun that names its job.
3. In prose: "Plasmid Labs" (the org), "Plasmid" (the family), `plasmid-debug` (a tool, always in code format).
4. **CRYENGINE and Crytek never appear in a name, logo, package, repo, domain or handle.** They appear only as plain descriptive text ("Linux tooling for CRYENGINE") and always next to the disclaimer in section 7. Reason: Crytek's license grants the CRYENGINE and Crytek trademark rights "only to promote the Game" (clause 4.1), and a tooling project is not a Game. So we rely on plain descriptive reference plus a disclaimer, not on a license. This is a working rule, not legal advice.
5. Code identifiers: C++ `Plasmid::<Module>` with headers under `plasmid/<module>/` (for example `Plasmid::Debug`, `<plasmid/debug/Debug.h>`), Python `plasmid_<module>`. Console commands and CVars start with `plasmid_`, lowercase with underscores (`plasmid_debug_*` for plasmid-debug, `plasmid_*` for plasmid-mcp).
6. Each tool's CLI is `plas-<module>` (`plas-dev`, `plas-assets`, `plas-mcp`). A bare `plas` is never a published package, repo or command name.
7. Registries: publish as `plasmid-*`. The bare `plasmid` name on npm is taken (an unrelated gossip-protocol library, v0.0.0) and must never be depended on. As of 2026-10-26 the bare name was free on PyPI and every `plasmid-*` name checked was free on both.
8. Every repo carries "by DNAngeluS", set with the official wordmark: `brand/dnangelus-wordmark.svg` (dark) and `brand/dnangelus-wordmark-light.svg`, outlined exports of `.dna-wordmark` from `dna.css`. On the web use the original markup, `<span class="dna-wordmark"><span class="halo">DNA</span>ngelu<span class="end">S</span></span>`. Never redraw it by hand.

## 3. Voice

Inherited from dnangelus.ar: terse, concrete, lowercase-leaning, terminal metaphors, honest about state. The site's own lines set the register: "I build tools that bite back." "builder of small, sharp things." "// no tracking, no cookies, no nonsense."

| Do | Don't |
|---|---|
| Say what it does and what state it is in: "0.1.0. The console layer works." | "Powerful, next-gen toolkit" |
| Name the thing that was verified, and where: "tested on 5.6.7, Arch, X11" | "Works everywhere" |
| Short verbs: build, run, splice, pin | Hype, exclamation marks, emoji |
| Admit the gaps: "planned", "not verified" | Roadmap promises with dates |

Lines to reuse:

- Tagline (decided 2026-11-10): **Splice into the engine.**
- Supporting line, for when there is room under the tagline: **Lives beside the engine. Never rewrites it.**
- Descriptor (with the disclaimer): **Linux tooling for CRYENGINE.**
- Status words, as on the site's badges: `idea`, `wip`, `shipped`, `archived`.
- `// ` as an aside marker belongs in UI and terminals, not in READMEs.

## 4. Logo

### 4.1 Idea

One ring, one insert. Plasmid maps are rings with features marked on them; the mark is that ring with one piece spliced in. The ring is the host (cyan) and is broken where the insert goes. The insert (magenta) is an arc that sits just outside the ring line, offset, so it reads as a different thing added on, not a segment of the same circle. That offset is what keeps it from reading as a loading spinner.

### 4.2 Construction

64-unit grid, centre (32, 32). Butt caps only: a cut end is the point.

| Part | Value |
|---|---|
| Host ring | radius 22, stroke 6 |
| Insert arc | radius 26, stroke 6 (outset 4 from the host centreline) |
| Insert span | 60° |
| Host break | insert span + 7° on each side (74° total) |
| Elements | exactly two paths. Nothing else. |

Reference implementation: `brand/mark-draft.svg` (dark) and `brand/mark-draft-light.svg`.

### 4.3 Identity by position

The root mark has its insert at 12 o'clock (0°). Each tool takes a diagonal, clockwise, in README order:

| Mark | Insert position |
|---|---|
| plasmid | 0° |
| plasmid-dev | 45° |
| plasmid-assets | 135° |
| plasmid-debug | 225° |
| plasmid-mcp | 315° |

Rules: the insert never sits off this grid. A fifth tool needs a design pass, not improvisation. **Below 32px every tool uses the root orientation.** At 24px the diagonal positions stop being reliable (checked on the reference sheet).

### 4.4 Colour

| Surface | Host | Insert | Contrast |
|---|---|---|---|
| Dark (default) `#07080d` | `#22e5ff` | `#ff2bd6` | host 13.07:1, insert 6.26:1 |
| White `#ffffff` | `#05060a` | `#b01c95` | host 20.25:1, insert 6.09:1 |
| GitHub light `#f6f8fa` | `#05060a` | `#b01c95` | insert 5.72:1 |
| One colour | `#e6ecff` on dark, `#05060a` on light or on cyan | same | |

Cyan against magenta is only 2.09:1. **Colour never carries the host/insert separation on its own.** The gap and the 4-unit outset do. Every one-colour version must still read as a ring with a spliced piece.

On light surfaces, bright cyan (1.53:1) and bright magenta (3.20:1) fail. Never use them there.

### 4.5 Wordmark

`plasmid` in JetBrains Mono 700, lowercase, letter-spacing -0.02em (the same as `.dna-wordmark`). Letters in ink (`#e6ecff` dark, `#05060a` light). **The final `d` takes the insert colour.** It is the same end-of-word rule as the DNAngeluS wordmark, and the `d` carries a closed loop of its own.

Tool lockups: `plasmid` as above, then the suffix (`-dev`) in muted ink (`#8b95b8` dark, `#57606a` light, 6.39:1 on white). Only the `d` of plasmid is ever magenta. Tagline in Space Grotesk 400.

### 4.6 Lockups and space

- Horizontal: the mark is about 1.3× the wordmark's font size, and the gap between them is roughly a third of the mark's height.
- Stacked: mark above the wordmark, centred, tagline below.
- Endorsement: below or beside the lockup, `by` in muted ink followed by the DNAngeluS wordmark at no more than half the plasmid wordmark's font size. The official wordmark's halo rises about 0.26em above its box, so leave that room.
- Clear space: at least 25% of the mark's height on every side.
- Minimum sizes: mark alone 16px (root orientation); a lockup needs a wordmark of at least 14px.
- Avatars: the root mark on `#07080d`, about 60% of the square, centred. It survives a circular crop.

### 4.7 Never

- Swap the colours, fill the ring, close the gap, or rotate the insert off the grid.
- Add gradients, outlines, 3D or extra strokes.
- Use glow below 48px, in print, or in icons. Glow is for web heroes.
- Put a double helix inside or around the ring. The helix belongs to DNAngeluS, the parent. The ring is Plasmid's.
- Use syringes, vials, hypodermics, Art Deco or any BioShock vocabulary. "Plasmid" already collides with that game, and the visuals must not add to it.
- Use CRYENGINE or Crytek logos, engine icons or screenshots in the mark or lockups.
- Redraw the DNAngeluS wordmark.

## 5. Design system

### 5.1 Extend, don't fork

Plasmid uses the DNAngeluS tokens as they are. The source of truth is `assets/dna.css` and the `:root` block in `index.html` on dnangelus.ar. `brand/tokens.css` is a copy for docs and offline use. Plasmid adds only two things: semantic aliases, and `pls-*` components that have no `dna-*` equivalent.

### 5.2 Tokens (inherited)

| Group | Tokens |
|---|---|
| Surfaces | `--bg #07080d` · `--surface #0d1018` · `--surface-2 #141826` · `--border #232a3d` · `--border-strong #5a6690` |
| Ink | `--ink #e6ecff` · `--ink-muted #8b95b8` |
| Accents | `--cyan #22e5ff` · `--cyan-dim #1596ab` · `--magenta #ff2bd6` · `--magenta-dim #b01c95` |
| On-accent | `--on-cyan #05060a` · `--on-magenta #05060a` |
| Status | `--success #5cffb0` · `--warning #ffc247` · `--danger #ff5470` |
| Type | JetBrains Mono (`--font-mono`), Space Grotesk (`--font-sans`) · sizes 12, 14, 16, 20, 28, 40 |
| Space | 4, 8, 12, 16, 24, 40, 64 (`--space-1` … `--space-16`) |
| Radius | 2, 6, 12 |
| Glow | `0 0 24px 0` at 35% cyan or magenta |
| Motion | 150ms ease. Cursor blink 1.1s `steps(1)`. Respect `prefers-reduced-motion`. |

### 5.3 Semantic roles (the additions)

- `--host` = cyan. What already exists: links, primary buttons, static emphasis, the ring.
- `--insert` = magenta. What is being spliced in: hover, active, selected, added lines in a diff. Focus is not an insert: it keeps the DNAngeluS cyan outline (`:focus-visible`, 2px, offset 2px).
- `--host-dim` and `--insert-dim` for fills and borders.
- Status colours follow the site's badges: `idea`, `wip`, `shipped`, `archived`.

### 5.4 Contrast (computed, WCAG)

| Pair | Ratio |
|---|---|
| ink on bg | 16.97:1 |
| cyan on bg | 13.07:1 |
| ink-muted on bg | 6.75:1 |
| magenta on bg | 6.26:1 |
| on-cyan on cyan (button) | 13.23:1 |
| on-magenta on magenta (button) | 6.33:1 |
| border-strong on bg | 3.56:1 (borders and graphics only) |
| cyan vs magenta | 2.09:1 (never rely on it) |
| success / warning / danger on bg | 15.61 / 12.44 / 6.44:1 |
| cyan-dim on white | 3.51:1 (graphics only, not text) |

### 5.5 Components

Reuse every `dna-*` class as is: buttons, links, tags, badges, cards, the terminal window, nav, stats, form fields, the `// ` section heading. The `dna-helix` strip stays a DNAngeluS element and does not appear on Plasmid surfaces. New components need a reason and the `pls-` prefix. Two are specified so far:

- `pls-tool`: a `dna-card` carrying a 32px mark at the tool's position, the tool name in code, a `dna-tag` with the version, and a `dna-badge` with the status.
- `pls-lockup`: the header lockup from 4.6.

One signature motion: on load, the insert slides into place from 30° before its resting position, 400ms ease-out, once. Off under reduced motion.

### 5.6 Surfaces

Dark first. Light exists for GitHub light mode and print, using the host and insert colours in 4.4. DNAngeluS itself is dark-only, so the light tokens in `brand/tokens.css` are a Plasmid extension.

### 5.7 README conventions

Tool name in code format. Status line first. A "verified on" line. No emoji. At most three badges (license, version, status).

## 6. Open decisions

Decided 2026-11-10: the tagline is "Splice into the engine."

- The copyright line in LICENSE: personal name or a studio. Check ownership if any of this was written on company time.
- The position rule for a fifth tool.
- A free trademark search for "Plasmid" in software classes 9 and 42 before launch.
- Upstream, in `dna.css`: the `.halo::before` ellipse is content-box (the global `box-sizing` reset skips pseudo-elements), so its border adds to the `.2em` height, and its `1.5px` border renders as 1px on a 1x screen. The SVG wordmark export keeps the nominal 1.5px and the content-box height.

## 7. Publishing checklist (every plasmid-* repo)

Crytek's license forbids distributing CRYENGINE itself, its Tools and its Documentation (clause 2.4). Before any repo goes public:

- [ ] No CRYENGINE source, headers, assets, documentation or Sandbox editor code in the tree or the history.
- [ ] No patch or diff files against engine source. Engine-side fixes go to handoff notes, not to a public repo.
- [ ] Any private engine runtime copy (for example a `.engine-private/` folder) is gitignored. Scan the whole history of a repo that predates this org for engine binaries (`libCry*`), shader caches and copied engine files before its first public push.
- [ ] No assets copied from reference projects with no license (for example GameSDK-Island).
- [ ] Third-party dependencies listed, with licences compatible with MIT.
- [ ] README says what is verified, on what, and what is planned.
- [ ] The disclaimer is present: "CRYENGINE and Crytek are trademarks of Crytek GmbH. Plasmid is an independent project, not affiliated with or endorsed by Crytek."
- [ ] "by DNAngeluS" line present.

None of this is legal advice. For the trademark and engine-patch questions in particular, a short review by a lawyer, or a question to Crytek, is cheaper than finding out later.

## 8. Brand assets and the MIT license

The MIT license covers the code and documentation. It does not grant the right to present other projects as Plasmid or as made by DNAngeluS. Forks are welcome; they should use their own name and mark.
