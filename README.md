# SortedBags

A bag and bank sorter for WoW Classic Era with Retail-style per-bag categories. Right-click a bag portrait to make it the home for Gear, Consumables, Reagents and more.

## Features

- **Per-bag categories** — assign any combination of categories to each bag through its portrait menu
- **Specialty bags respected** — arrows go to quivers, soul shards to soul bags, herbs to herb bags, before anything else
- **Bank sorting** — with the bank open, sorting sorts the bank too. Nothing is deposited or withdrawn.
- **Ignore a bag** — tick Ignore Bag and nothing moves in or out of it
- **Hearthstone and Mount pinning** — pin them to a bag's first slots so you can grab them without looking
- **Fast** — event-driven batching, so sorting costs no FPS
- **Safe** — refuses to start in combat, with an item on the cursor, or with the trade or auction window open

## Installation

1. Copy the `SortedBags/` folder into `World of Warcraft/_classic_era_/Interface/AddOns/`.
2. Restart the game or `/reload`.
3. Enable **SortedBags** in the AddOns list.

## Usage

- Open your bags (`B`). The sort icon sits left of the gear icon under the backpack's close button. Click it, or type `/sortbags`.
- The gear icon, or `/sb`, opens the options window.
- **Right-click any bag's portrait** to open its category menu.
- Toggle bank sorting with **Also Sort Bank** in the backpack's right-click menu.

## Categories

Listed in the priority order the sorter uses:

| Category | Covers |
| --- | --- |
| Hearthstone | Pinned to the bag's first slot |
| Mount | Pinned next, after the Hearthstone if both are set |
| Reagents | Class spell components: Soul Shards, Symbol of Kings, Ankhs, Holy Candle |
| Consumables | Food, drink, potions, scrolls |
| Gear | Weapons and armor, weapons first |
| Trade Goods | Cloth, herbs, ore, leather, enchanting mats, recipes |
| Quest Items | Quest items |
| Miscellaneous | Keys, containers, projectiles, pets, holiday tokens |
| Junk | Grey items, which win over every class category |

Reagents and Trade Goods are deliberately separate: Reagents is the item class for spell components an ability consumes, Trade Goods is the profession-mats class. Enchanting dusts and essences are Trade Goods.

A bag with a category assigned shows a subtle desaturation on its portrait. **Reset bag categories** clears every flag on that bag.

## Sort order

1. Specialty bags claim their matching items first — a hardware constraint from the bag itself, not configurable.
2. Each tagged bag claims its matching items, in the category order above.
3. Unassigned bags absorb everything else.
4. Leftovers spill into any category bag with empty slots left.

Within a category, items sort by class, sub-class, quality (highest first), then name. Within every bag, items fill top-left to bottom-right.

## Options (`/sb`)

- **Sort Right to Left** — which bag fills first, not the slot order inside it. On: backpack, then bag1 to bag4. Off (default): bag4 down to the backpack.
- **Loot Right to Left** — fills incoming loot right to left. Uncheck for left to right.

## Requirements

WoW Classic Era 1.15.x. Sorts the backpack and four bag slots, plus the bank when it is open.

## Credit

The specialty-bag planner is ported from [shirsig's SortBags](https://github.com/shirsig/SortBags) under its original license. SortedBags replaces the original hand-tuned sort buckets with per-bag category flags modelled on Retail's `Enum.BagSlotFlags`, and adds the right-click portrait menu.
