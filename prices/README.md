# Prices and production

India's official price and production indices, month by month: consumer prices (CPI) for every State, rural and urban, down to single items; wholesale prices (WPI) for every item; and the Index of Industrial Production (IIP).

Latest month: 2026-10.

## At a glance

| Table | Rows | Period | Where |
| --- | ---: | --- | --- |
| cpi | 4,13,436 | 2011-01 to 2025-12 | `data/cpi/` (15 files) |
| cpi-back-series | 52,863 | 2011-01 to 2013-05 | `data/cpi_back_series.csv` |
| cpi-items | 42,159 | 2014-01 to 2025-12 | `data/cpi_items/` (12 files) |
| cpi-2024 | 44,088 | 2025-01 to 2026-10 | `data/cpi_2024/` (2 files) |
| cpi-2024-states | 2,420 | 2025-01 to 2026-10 | `data/cpi_2024_states/` (2 files) |
| cpi-2024-back-series | 432 | 2013-01 to 2024-12 | `data/cpi_2024_back_series.csv` |
| wpi-2011-12 | 1,46,861 | 2012-04 to 2026-04 | `data/wpi_2011_12/` (15 files) |
| wpi-2022-23 | 48,891 | 2023-04 to 2026-10 | `data/wpi_2022_23/` (4 files) |
| iip-monthly | 17,196 | 1994-04 to 2026-09 | `data/iip_monthly/` (33 files) |
| iip-annual | 1,405 | 1994-95 to 2025-26 | `data/iip_annual.csv` |

## Spreadsheet-friendly files

The same data, one row per item and one column per period, for spreadsheets.

- `data/wide/cpi_headline.csv`: All-India consumer price inflation each month: combined, rural and urban
- `data/wide/cpi_inflation_by_state.csv`: Consumer price inflation each month (combined, per cent), one column per State or UT

## Files

Each table is in `data/` as CSV, one file per calendar year where it is large.

| Table | | Covers | Rows |
|---|---|---|---|
| `cpi` | Consumer prices (base 2012), by State, rural and urban, group and subgroup | 2011-01 to 2025-12 | 4,13,436 |
| `cpi_back_series` | Consumer prices back series on base 2012, as MoSPI publishes it beside the main series | 2011-01 to 2013-05 | 52,863 |
| `cpi_items` | All-India consumer prices of each item (base 2012) | 2014-01 to 2025-12 | 42,159 |
| `cpi_2024` | All-India consumer prices on the new base 2024, down to each item | 2025-01 to 2026-10 | 44,088 |
| `cpi_2024_states` | Headline consumer prices on base 2024 for every State and UT | 2025-01 to 2026-10 | 2,420 |
| `cpi_2024_back_series` | Headline consumer prices on base 2024, linked back to earlier years | 2013-01 to 2024-12 | 432 |
| `wpi_2011_12` | Wholesale prices (base 2011-12), by group down to each item | 2012-04 to 2026-04 | 1,46,861 |
| `wpi_2022_23` | Wholesale prices on the new base 2022-23, by group down to each item | 2023-04 to 2026-10 | 48,891 |
| `iip_monthly` | Industrial production each month, by sector, use and industry | 1994-04 to 2026-09 | 17,196 |
| `iip_annual` | Industrial production each financial year | 1994-95 to 2025-26 | 1,405 |

Columns are described in `codebook.csv` and `datapackage.json`.

## Quick start

```python
import pandas as pd

base = "https://raw.githubusercontent.com/knowmoreindia/open-data/main/prices/data"
cpi = pd.read_csv(f"{base}/cpi/2025.csv")
headline = cpi[(cpi.state == "All India") & (cpi.subgroup == "General-Overall")]
```

## Worth knowing

- CPI moved to base 2024. The new series (`cpi_2024` tables) starts in 2025-01; the base 2012 series (`cpi`) runs to 2025-12. The two are on different scales.
- WPI moved to base 2022-23. The new series starts in 2023-04; the base 2011-12 series runs to 2026-04.
- IIP has several base years over time (1993-94, 2004-05, 2011-12, 2022-23); `base_year` says which.
- Figures are as published, including provisional ones, which are revised later.

## How to cite

Know More India, *Prices and production*, version 2026-11-26, https://github.com/knowmoreindia/open-data/tree/main/prices. Licensed CC BY 4.0.

```bibtex
@misc{knowmoreindia_prices,
  author = {{Know More India}},
  title = {Prices and production},
  year = {2026},
  version = {2026-11-26},
  howpublished = {\url{https://github.com/knowmoreindia/open-data/tree/main/prices}}
}
```

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Credit: Know More India, from MoSPI and the Office of the Economic Adviser, DPIIT.
