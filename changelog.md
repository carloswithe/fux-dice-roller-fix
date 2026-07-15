# FUx Dice Roller Change Log
## Version 0.4.3 (2026-07-14) - fux-dice-roller-fix
- Added the required `id` field to module.json (Foundry v10+ install fix)
- Foundry v13 (13.351) compatibility:
  - Listen on both `renderChatMessage` and `renderChatMessageHTML` for blind-roll hiding
  - Rewrote the chat sidebar dice icon injection without jQuery, and made it fail
    silently (falls back to the `/fux` chat command) if the sidebar DOM layout changed
  - Dropped the deprecated `{async: true}` option from `Roll#roll` calls
  - Read `game.user.character.img/name` directly instead of the removed `.data` wrapper
  - Use `CONST.CHAT_MESSAGE_STYLES` (with a v10/v11 fallback to `CHAT_MESSAGE_TYPES`)
    and set `ChatMessageData.style` alongside the deprecated `.type` field
  - Use `foundry.applications.handlebars.renderTemplate` with a fallback to the
    deprecated global `renderTemplate`
- Bumped `compatibility.verified`/`maximum` to 13; `minimum` stays at 10

## Version 0.4.2 (2023-10-18)
- Updated for Foundry version 10 and 11

## Version 0.4.1 (2022-01-xx)
- Updated FU v2 Combat Helper

## Version 0.4.0 (2022-01-21)
- Added Reset dice selection to diceroller
- Added persistance to dice selection

## Version 0.3.0 (2022-01-20)
- Added option for custom Action/Danger icon
- Updated FU v2 Combat Helper
- Minor fixes

## Version 0.2.0 (2022-01-19)
- Added system variant Earthdawn Age of Legend
- Minor fixes

## Version 0.1.0 (2022-01-17)
- First release
