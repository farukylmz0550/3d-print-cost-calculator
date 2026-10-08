# 3D Printer Cost Calculator

> A single-file, offline-friendly tool that works out the true cost of a 3D print — and the price you should sell it for.

Open it in your browser, enter your fixed settings once (filament price, electricity, waste allowance, profit margin, amortization) and save them as a profile. From then on, just type each print's weight and duration and press **Calculate**.

---

## Features

| | |
|---|---|
| 🧮 **Transparent breakdown** | Filament, electricity and amortization shown as separate line items |
| 🏷️ **Cost ≠ profit** | Production cost (profit excluded) and profit margin on their own lines; sale price at the bottom |
| 💾 **Profiles** | Save/load/delete your fixed settings under a name — stored in your browser |
| 💱 **Currency** | ₺, $, € or £ — saved with the profile |
| 🌍 **TR/EN** | Turkish and English interface, one-click switch |
| 🌓 **Two themes** | Fine Porcelain × Burnt Ochre (light) · Ink & Copper (dark) |
| 🔒 **Privacy** | Nothing leaves your device — no server, no account, no cookies |
| ⚡ **Single file** | `index.html` — double-click and it works |

## The Calculation

```
Filament        = print weight ÷ 1000 × price per kg × (1 + waste%)
Electricity     = (printer power ÷ 1000) × print duration × kWh price
Amortization    = fixed amount
──────────────────────────────────────────────────────────────
Production cost = filament + electricity + amortization   (excludes profit)
Profit margin   = production cost × profit %
Sale price      = production cost + profit margin
```

**Example:** 85 g PLA, 6.5 h print; filament 650 ₺/kg, 150 W, electricity 2.55 ₺/kWh, 5% waste, 30% profit, 10 ₺ amortization →

| Item | Amount |
|---|---:|
| Filament | 59.61 ₺ |
| Electricity | 2.49 ₺ |
| Amortization | 10.00 ₺ |
| **Production cost** | **72.10 ₺** |
| Profit margin (30%) | 21.63 ₺ |
| **Sale price** | **93.73 ₺** |

## Usage

1. Open `index.html` in any browser.
2. Fill in the **Fixed Settings** and pick a **Currency** (₺ / $ / € / £).
3. Enter the weight and duration from your slicer under **Print Details**, press **Calculate**.
4. Save your settings under a name in **Profiles**; keep separate profiles for different materials or prices.
5. Use **Export** to back up all profiles as JSON, **Import** to restore them elsewhere.
6. Switch the interface language with the **EN/TR** button in the top right.

## Design

The interface follows the **UI Design Language** document of the [Book Shelf](https://github.com/farukylmz0550/bookshelf-web) project:

- **Theme 1 — Fine Porcelain × Burnt Ochre:** `#FAF0E1` background, `#BB4F35` accent; warm and calm
- **Theme 2 — Ink & Copper:** `#1D2020` background, `#C17A5E` accent; dark and deep
- **Typography:** Noto Serif (headings) · Noto Sans (interface) · Noto Sans Mono (numeric values)
- **Geometry:** 4/8/12 px radius family, plain borders, restrained shadows

Deliberately **avoided**: glassmorphism, gradient-heavy "modern" templates, generic SaaS dashboard looks, unnecessary card piles.

> Principle: *Clarity before decoration.*

## Technical Notes

- A single `index.html`; no dependencies, no build step, no server
- Profiles live in `localStorage`; the language, theme and currency preferences do too
- Number formatting follows the interface language: `tr-TR` (72,10 ₺) / `en-US` (72.10 $)
- Noto fonts load from Google Fonts (falls back to system fonts offline; the page keeps working)
- Supports `prefers-reduced-motion`, keyboard navigation and `aria-live` result updates

## License

This project is released under **CC0 1.0 Universal** (public domain) — see [LICENSE](LICENSE).

You can copy, modify, distribute and use it, even commercially, without asking permission.
