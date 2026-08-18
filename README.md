
# Kanto Companion Mobile

Forked from Discord user Matthew's existing mod, Kanto Companion (Desktop Version)

An in-game companion that loads directly on top of the game, built for
controller and touch play on a smaller screen. All screens have been optimized for a smaller display, specifically the Odin 2 Portal. The item screen has been majorly overhauled to work with a controller as well as touch controls. Instead of relying on keyboard keys for hotkeys, now R2 opens the overlay, X opens the item bag/PC screen, and Y opens the party/box screen. There is also an option to enable touch controls that will add two navigation buttons to the screen and add a transparency to the overlay so you can still see the touchpad.

> **Fan-made; not affiliated with or endorsed by Nintendo / Game Freak / The Pokémon Company.**

## Not yet fully compatible with Gen 2
Expect it to be broken in Gold

*******AI USE DISCLAIMER******* This is developed with AI just like it's original version. If you do not support AI in mods that is fine. Take it or leave it.

## Controls

| Button | Action |
| --- | --- |
| **R2** | Toggle the live **overlay** (off by default), from the overworld, the overlay itself, or the Party screen. On the Items screen, R2 instead adjusts a held stack's quantity, so it doesn't also switch there. |
| **X** | Open the **Items** screen (move items between your Bag and the PC). |
| **Y** | Open the **Party / Boxes** screen (deposit, withdraw, rearrange, swap Pokémon). |
| **B** | Close whichever screen is open. The overlay itself only closes with **R2** again, or by opening Items/Party. |

- **Touch screen nav buttons** (off by default — enable in mod options,
  "TOUCH SCREEN NAV BUTTONS"): two transparent left/right arrow buttons,
  positioned just above where Start/Select appear on Gen1Recomp's built-in
  touch control layout, step through overlay → Items → Party/Boxes →
  closed — left goes backward, right goes forward. When this is on, the
  Items and Party/Boxes screens also widen the gap between their two
  panels so neither one sits under a button.
- **Left stick cursor** (always on): on the Items or Party/Boxes screen,
  pushing the left stick brings up a free-moving cursor (a small gold
  circle); A/B click/cancel just like touch — including on the Party
  screen, which the D-pad row-cursor doesn't cover (grabbing and dropping
  a Pokémon). Push far enough to start a drag, or tap A to pick something
  up and tap it again to place it. It only takes over once you push the
  stick, and D-pad or direct touch hand control straight back — all three
  ways of controlling the screen work side by side.

The Items and Party/Boxes screens open only from the overworld; while one
is up, the game pauses and all input goes to the screen. Press the same
button again, or **B**, to close.

## Overlay — R2

- **Left:** your party — sprite, HP bar (animated), XP-to-next, level,
  status, types, and moves + PP. The mon that's out in battle is
  highlighted.
- **Right:** trainer info (money, play time, badges, dex) + route
  encounters (grass/surf with %, level ranges, sprites). During a battle
  this swaps to a battle readout: your best moves ranked by effectiveness
  + STAB, the enemy's super-effective threats, a speed indicator, and —
  in wild battles — live per-ball catch odds at the target's current
  HP/status.

The overlay is read-only. Panels are anchored to the left/right edges and
scale to your window (designed against 1440p); since the game renders
widescreen, they sit over the sides of the view. When **TOUCH SCREEN NAV
BUTTONS** is on, the overlay also dims to about 60% opacity so the touch
controls underneath stay visible through it.

## Items (Bag ⇄ PC) — X

- **Drag** an item to the other side, or tap it then tap the other side.
  Reordering within a side works the same way.
- Picking up a stack takes the whole stack.
- **Controller:** **D-pad left/right** picks which side (Bag or PC) is
  focused — it gets a gold outline. **D-pad up/down** moves a
  gold-outlined cursor row by row through the focused side's list. Press
  **A** to pick up the highlighted item (armed immediately, no need to
  drag), then **D-pad** to wherever it should land — the **same** side to
  reorder it in place, or **left/right** to the **other** side to
  transfer it — with up/down there picking exactly where in that list
  it'll land, including one slot past the last item to drop it at the
  **end of the list** — and **A** again to drop it (landing back on its
  own row is a no-op). **L2/R2** adjusts the quantity of a held stack, so
  up/down stays free to pick a drop spot even mid-stack. **B** cancels a
  pending pickup; with nothing held, it closes the screen. Or push the
  **left stick** for a free cursor — see above.
- **Sort** each side by Type / A–Z / Qty (view only). On the **Bag** you
  can **Save order** to make it stick in-game (with a controller: **D-pad
  up** from the top row of the Bag list selects it, **A** saves, **D-pad
  down** returns to the list); the in-game **PC is always A–Z**, so its
  sort is browsing-only.
- A destination that can't accept the item turns **red** with the reason
  (bag/PC full, stack maxed).

## Party / Boxes — Y

- **Left:** your party (up to 6) with HP. **Right:** a rail of all 12
  boxes plus the selected box as a sprite grid. Tap a box tab, or (with a
  controller) press **D-pad left/right**, to switch boxes.
- **Grab** a Pokémon and drop it on a slot or a box tab to deposit /
  withdraw / move between boxes. Dropping onto an **occupied** slot
  **swaps** the two.
- **Controller:** the D-pad only switches boxes here — for grabbing and
  dropping a Pokémon, push the **left stick** for a free cursor, same as
  Items above.
- Rules are enforced: boxes hold 20, the party holds 6, you can't deposit
  your last Pokémon, and the party is **never left without a healthy
  Pokémon** (a swap that brings a healthy one in is fine).

## Debug input HUD (Android / no log access)

Since v2.4.0, a small "last input -> ..." readout appears in the
bottom-left corner for a few seconds after any button, gamepad input, or
raw touch event — useful for confirming exactly what a control reports,
without needing a computer to read logs. Off by default; it's a toggle in
the **F10 mod manager** — open the manager, select **Kanto Companion**,
and flip **DEBUG INPUT HUD** on (e.g. when positioning the touch nav
buttons on a new device). No file editing or restart needed; it takes
effect immediately.

As of v2.4.1, raw touches also show as a **percentage of the current
window size**, e.g. `touch: 392,406 (20.4%,37.6% of 1920x1080)`, not just
raw pixel coordinates — raw pixels only mean something on the exact
screen they were measured on, so percentage is what actually carries over
to a different screen size or resolution. This is the same
percentage-of-window approach `TOUCH_NAV_LEFT`/`TOUCH_NAV_RIGHT` in
`main.lua` use to position the touch nav buttons — if they land somewhere
awkward on your device, tap around where you'd expect them and read the
percentage off the HUD to retune the bounds.

## Install

Copy this whole folder into `%APPDATA%\pokemon-love2d\mods\`, launch the
game, and enable **Kanto Companion** in the **F10** mod manager.

## Notes

- Ships no game assets: sprites and the badge sheet are read from your
  own game install at runtime, and it uses LÖVE's built-in font. A few
  symbols the font lacks (♀/♂, some battle glyphs) are shown as safe text
  equivalents.
