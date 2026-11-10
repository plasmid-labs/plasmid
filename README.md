<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="brand/mark-draft.svg">
    <img src="brand/mark-draft-light.svg" width="96" alt="Plasmid mark: a ring with one piece spliced in">
  </picture>
</p>

<h1 align="center">plasmid</h1>

<p align="center"><strong>Splice into the engine.</strong><br>Linux tooling for CRYENGINE, by <a href="https://dnangelus.ar">DNAngeluS</a>.</p>

---

Small tools that live beside CRYENGINE and never rewrite it. Build it, run it, debug it and drive it from a Linux box, without touching the engine itself.

Each tool is its own repo with its own version, changelog and tag. This repo is the front door: what exists, what state it is in, and the rules every tool follows.

**Status: early.** Tools go public one at a time, when each is ready to be used by someone who is not me. The names below are reserved under [plasmid-labs](https://github.com/plasmid-labs); links appear here when a repo is public.

## Tools

| Tool | What it does | State |
|---|---|---|
| `plasmid-dev` | Dev runner for CRYENGINE game projects. One `make` UX (`doctor`, `setup`, `run`, `stop`, `status`, `logs`), a SPIR-V shader server (Wine or native `dxc`) and tagged vendoring. CLI: `plas-dev`. | 2.2.1 |
| `plasmid-assets` | Asset writers in Python: PNG to DDS, static-mesh CGF, glTF to CGF and skinned CHR, mesh optimization and LODs (Blender-backed), particles, Schematyc, audio, terrain. CLI: `plas-assets`. | 0.21.2 |
| `plasmid-debug` | Debug kit for game plugins in C++. Extends the engine's own console with `plasmid_debug_*` commands and CVars; header-only orbit camera. Render views, screenshots, pause and free camera are planned. | 0.3.0 |
| `plasmid-mcp` | An MCP server plus an in-engine plugin so an LLM client can build, run and observe CRYENGINE scenes on Linux, as an alternative to the Sandbox editor workflow. CLI: `plas-mcp`. | 0.9.2 |

## Rules every tool follows

- **The engine stays read-only.** Tools extend CRYENGINE through its own interfaces. Nothing here patches it.
- **Everything is reachable the same way.** Where a tool exposes behaviour inside the engine, it is a console command or a CVar, so the in-game console, the remote console, an MCP client and `+cvar` launch arguments all hit the same thing.
- **Pinned, never edited.** A project that needs a tool carries a tagged copy. A vendored copy is never edited; fixes go back to the tool.
- **Linux first.** No Windows dependency at run time.

## What you need

Plasmid does not include CRYENGINE and grants no rights to it. You need your own copy and you must accept [Crytek's license](https://www.cryengine.com/ce-terms), which, among other things, limits CRYENGINE to developing games and sets royalties on what you ship. That is between you and Crytek.

Tools target CRYENGINE 5.7.1 and 5.6.7; check each tool's README for which one it defaults to. Plasmid contains no CRYENGINE code, and the engine-side changes needed to build on Linux are out of scope and not distributed here.

## License

[MIT](LICENSE). The name and mark are covered by [BRAND.md](BRAND.md), which also holds the design rules.

CRYENGINE and Crytek are trademarks of Crytek GmbH. Plasmid is an independent project, not affiliated with or endorsed by Crytek.

---

<p align="center">
  <sub>by</sub>
  <a href="https://dnangelus.ar">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="brand/dnangelus-wordmark.svg">
      <img src="brand/dnangelus-wordmark-light.svg" height="30" alt="DNAngeluS">
    </picture>
  </a>
</p>
