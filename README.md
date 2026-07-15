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

All other credit for the module goes to the original author.

## Compatibility

- Minimum: Foundry v10
- Verified: v11
- Maximum: v11

If you're on Foundry v12+, this module may not work correctly even with the `id` fix — the original manifest never declared v12 compatibility.

## Install

Use this manifest URL in Foundry's module installer:

```
https://raw.githubusercontent.com/carloswithe/fux-dice-roller-fix/main/module.json
```
