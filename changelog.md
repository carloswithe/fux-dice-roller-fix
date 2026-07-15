# FUx Dice Roller Change Log
## Version 0.4.5 (2026-07-14) - fux-dice-roller-fix
- Fixed a v13 regression introduced by the 0.4.3 patch itself: setting
  `messageData.type = rvalue` (a number like `0`) on `ChatMessage.create()` now fails
  Foundry v13's DataModel validation with `DataModelValidationError: type: "0" is not a
  valid type for the ChatMessage Document class`, because v13 repurposed the `type`
  field for its new ChatMessage sub-type system. Confirmed live via console error on
  Foundry v13.351. The numeric roll-style value is now only set via `.style`.

## Version 0.4.4 (2026-07-14) - fux-dice-roller-fix
- Fixed a pre-existing bug (present in every version, not v13-specific): `RollFuxDice`
  read a `.roll-type-select` element that only exists inside the dice roller form's own
  template. Calling the `/fux [x]a[y]d` chat command without that form open threw
  `TypeError: Cannot read properties of undefined (reading 'value')` and silently did
  nothing. It now falls back to the chat log's own current roll mode
  (`game.settings.get("core", "rollMode")`) when the form isn't open — the same source
  Foundry's own `/roll`, `/gmroll`, `/blindroll` commands use.

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
