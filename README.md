# FakeDonald's Inventory Manager (CLI)

A terminal-based inventory tool built for a restuarant to keep track of stock, place orders, and log waste - all through a simple numbered menu. No database, no server, just Python and a CSV file.

---

## Why I Built This

Managing stock on a spreadsheet is fine until someone forgets to update it. This script puts everything in one place - you open it at the start of the shift, punch in your current box counts, and it tells you what's running low before you even ask. Orders come with GST calculated automatically, and waste gets logged with a dollar value so you actually know it.

---

## What It Does

- **Inventory view** - Shows all items with box count, price per box, and per-unit cost
- **Low stock alerts** - Fires automatically on startup and whenever you check inventory; each item has its own critical threshold
- **Daily inventory entry** - Replace stored quantities with today's actual counts
- **Order placement** - Pick items, enter box quantities, get a receipt with subtotal + 5% GST + total
- **Waste logging** - Enter units wasted per item and see the total dollar value lost
- **Save to CSV** - All changes persist back to `inventory.csv` when you exit properly

---

## Getting Started

### Requirements

- Python 3.x (no external libraries needed - just the standard `csv` module)

### Setup

1. Make sure `inventory.csv` is in the same folder as the script. It needs these columns:

```
name,quantity,price,units_per_box,critical_level
```

Example row:
```
burger bun,5,7.85,144,2
```

2. Run the script:

```bash
python mcd_inventory_critical_threshold.py
```

3. Use the menu:

```
1. View Inventory
2. Daily Inventory Entry
3. Place Order (with GST)
4. Log Wasted Products
5. Save and Exit
```

> **Always use option 5 to exit.** If you close the terminal without saving, your changes for that session are gone.

---

## File Structure

```
project/
├── mcd_inventory_critical_threshold.py   # main script
└── inventory.csv                          # your data file (required)
```

---

## CSV Format Reference

| Column | Description |
|---|---|
| `name` | Item name (e.g. `burger bun`) |
| `quantity` | Current boxes in stock |
| `price` | Price per box (CAD) |
| `units_per_box` | How many units in one box |
| `critical_level` | Box count that triggers a low stock warning |

---

## Notes

- The GST rate is set to 5% and can be changed at the top of the script (`GST_RATE = 0.05`)
- Per-unit price is calculated automatically from `price / units_per_box`
- If you enter letters where a number is expected, the program skips that item and moves on rather than crashing
- Don't edit `inventory.csv` while the program is running

---

## Author

Aayush Patel  
Built as part of a business inventory systems project
