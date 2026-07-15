# FUx Dice Roller (fixed fork)

This is a mirror of [FUx Dice Roller v0.4.2](https://github.com/Anderware/Foundry-Vtt-Sandbox-Macros/tree/main/Modules/FUx-Dice-Roller) by [anders-forslund](https://github.com/Anderware), republished here to fix a broken install via manifest URL.

## Fix applied

The original `module.json` only declared `"name"`, but Foundry v10+ requires a top-level `"id"` field to identify the package. Without it, installation fails with:

```
Module validation errors:
  id: may not be undefined
    at Module.installPackage (views.mjs:1:2203)
```

This fork adds `"id": "fux-dice-roller"` (matching `name`) and points `manifest`/`download`/`url`/`readme`/`changelog` at this repository so installs and update checks work correctly.

Versions 0.4.3-0.4.4 additionally patch the module for **Foundry v13 (tested against build 13.351)**. See [changelog.md](changelog.md) for the exact list of API changes handled (renamed hooks, removed `.data` wrapper, deprecated `Roll#roll({async:true})`, `CHAT_MESSAGE_TYPES` → `CHAT_MESSAGE_STYLES`, `renderTemplate` namespace move, and a pre-existing `/fux` chat-command crash that affected every prior version).

All other credit for the module goes to the original author.

## Compatibility

- Minimum: Foundry v10
- Verified: v13 (13.351)
- Maximum: v13

### Ways to open the dice roller on v13

- **"FU" icon next to the chat roll-mode buttons** (bottom of the chat tab, left of the globe/mask/eye/person icons) — restored in 0.4.7 to match the pre-v13 placement
- **Scene Controls** (left-hand toolbar, dice icon in the token tools group) — added in 0.4.6, uses a stable documented API
- **Settings → Configure Settings → Module Settings → FUx Dice Roller**
- **`/fux [x]a[y]d` chat command** (e.g. `/fux 2a1d`)

The Scene Controls button, Settings-menu launcher, and `/fux` command are confirmed working live on Foundry v13.351. The chat icon placement is based on the actual v13 chat-controls DOM (verified by inspecting a live 13.351 world) but is still pending a live click-test.

## Install

Use this manifest URL in Foundry's module installer:

```
https://raw.githubusercontent.com/carloswithe/fux-dice-roller-fix/main/module.json
```
