# Herorical Counts

A fast count sheet for comparing what your inventory system says you have against what you actually counted. It has two tools in one page: **Case Count** for items counted in cases and loose eaches, and **Weight Count** for items counted by the pound.

**Live:** https://allizine.github.io/work (the landing page; the tools are at `/counts.html`)

## What it does

Your system reports stock as decimal cases (for example 1.83 cases). You count the shelf in full cases plus loose eaches. This tool converts both to the same unit, shows the gap, and tells you whether you are short, over, or exact.

- Works on a phone or a desktop, with number keypads on mobile
- Search, add, and filter products (short, over, exact, not counted)
- Net variance across the whole count at the top of the page
- Print a clean count sheet or export a CSV
- Undo for deleted rows and cleared counts
- Everything saves automatically as you type

## How to use it

### Case Count

1. Tap **Add product** and enter a name and the units per case.
2. Enter the **System cases** your system shows. Decimals are fine.
3. Enter what you counted as **Counted cases** and **Counted eaches**. Use either one or both.
4. Read the result on the right: the gap in eaches, a Short, Over, or Exact label, and the exact numbers behind it.

### Weight Count

1. Tap **Add item** and enter a name.
2. Enter the **On hand (lbs)** from your system and the **Counted (lbs)** from the count.
3. Read the gap in pounds.

Press Enter to jump to the next field. Use the search box to find a product, and the filter buttons to focus on the ones that are short.

## How the math works

**Case Count**

```
System eaches   = system cases x units per case
Counted eaches  = (counted cases x units per case) + counted eaches
Exact gap       = counted eaches - system eaches
Gap in cases    = counted eaches / units per case - system cases   (the big number)
Gap in eaches   = exact gap rounded to the nearest whole each     (shown beside it)
```

Example: 0.89 system cases at 9 per case is 8.01 eaches. You count 7 loose eaches. The exact gap is -1.01 eaches, which is -0.1122 cases. The row shows **-0.11 cs** with **-1 ea** beside it, and the exact gap underneath so you can check the work.

When units per case is 1, a case and an each are the same thing, so the gap is shown exactly in cases with no rounding (for example 10.42 system cases and 8 counted is **-2.42 cs**). For everything else, the Short, Over, or Exact label follows the rounded gap in eaches, so a difference smaller than half an each shows as Exact.

**Weight Count**

```
Gap = counted lbs - on hand lbs
```

Weight is not rounded. It shows the exact gap to the hundredth of a pound.

**Net variance** is the sum of the gaps in eaches for every counted row.

## Printing and exporting

- **Print** builds a clean sheet of the current tab with every value, a summary, and the net variance. Case Count prints landscape and Weight Count prints portrait. For the cleanest page, turn off "Headers and footers" in your browser's print dialog.
- **Export CSV** downloads the current tab as a spreadsheet file that opens in Excel or Google Sheets.

## Where your data lives

Your counts are stored in your own browser on the device you are using. Nothing is sent to a server. That means:

- Counts do not move between devices or browsers
- Clearing your browser data erases them, so export a CSV if you need a record
- Private browsing windows do not keep data after they close

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The landing page that leads to both tools |
| `counts.html` | The tools: Case Count and Weight Count, in one file |
| `weight.html` | Redirects old links to the Weight Count tab |
| `LICENSE` | License terms |

## License

Copyright (c) 2026 Herorical. All rights reserved. This is proprietary software and no permission is granted to copy, modify, or redistribute it. See [LICENSE](LICENSE).
