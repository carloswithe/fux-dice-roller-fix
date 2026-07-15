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

### Known limitation

Foundry v13 rewrote the core chat sidebar with the new ApplicationV2 framework, and its internal HTML/class names could not be verified against a live v13 instance while patching this fork. The dice-roller icon injection into the chat sidebar controls is now defensive — if the expected DOM structure isn't found it fails silently instead of throwing, and the roller stays fully usable via the `/fux [x]a[y]d` chat command (e.g. `/fux 2a1d`) and via `game.settings.registerMenu`. If the icon doesn't appear next to the chat controls on your world, that's expected until someone confirms the current v13 DOM and the injection selector gets updated — please open an issue with a screenshot/HTML snippet of your chat sidebar controls if you'd like this fixed.

## Install

Use this manifest URL in Foundry's module installer:

```
https://raw.githubusercontent.com/carloswithe/fux-dice-roller-fix/main/module.json
```
