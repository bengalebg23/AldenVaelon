# HANDOFF: Vaelon Characters (bengalebg23/AldenVaelon)

Live at bengalebg23.github.io/AldenVaelon/. Single-file PWA: `index.html` + `sw.js` (network-first, CACHE `alden-vX.Y.Z`) + `manifest.json` + icons.

## Architecture
- `CHARS` at the top of the script holds one profile per character (`alden`, `ely`): stats, skills (0/1/2 = none/proficient/expertise), attacks, spells, gear, class-specific `ACTS()` rows, `FEATS`, `track()` (Combat tab resources), `fsum()`, `lore()`, rest hooks, quick-bar keys.
- `C` is the current profile. Shared code reads from it; `commonActs()` builds standard actions, grapple DC, Hit Dice and rests from C.
- Choice per phone: localStorage `dnd-char`. A phone with no choice and no old Alden data shows a "Who's playing?" picker and doesn't save or sync until one is chosen. Switching reloads the page.
- State per character: localStorage `<key>-state` / `<key>-at`; Firebase `aldenvaelon/state` (Alden, unchanged path) and `aldenvaelon/elyndra`. Last write wins by timestamp.
- Actions tab: four sections (Melee, Ranged, Bonus, Utility) with per-section toggles; a toggle only shows when both sides have items. `kind` on a row overrides attack/heal sorting; `togLabels` renames toggle options per character.
- Alden only: Savage Attacker (weapon dice rolled twice), Channel Divinity, spells. Elyndra only: Sneak Attack (+2d6 button, once-per-turn flag `saUsed`), Elven Accuracy (three d20s on attacks in Adv mode), Potion of Healing button.

## Feature history
- v1.0–1.4: Alden app, Firebase sync, Actions/Features tabs, filters, hide, quick bar, Savage Attacker.
- v1.5.0: multi-character profiles, picker and switcher, Elyndra added.

## Open threads
- Elyndra: backstory on her sheet stops mid-sentence; crossbow listed with arrows, not bolts; Noble background feature not printed on the sheet.
- Alden: Blue Dragon Infusion damage type (radiant vs lightning) to confirm with DM.
- Levelling up means editing the profile in `CHARS` (no in-app editor).
