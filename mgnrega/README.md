# MGNREGA

What the rural jobs scheme did in every district, every month since April 2018: person-days of work, households and individuals who worked, wages and spending, works started and finished, job cards, and work done by women, Scheduled Castes and Scheduled Tribes.

743 districts. Latest month: 2026-04.

## At a glance

| Table | Rows | Period | Where |
| --- | ---: | --- | --- |
| district-month | 69,407 | 2018-2019 to 2026-2027 | `data/district_month/` (9 files) |
| all-copies | 4,15,833 |  | release |

## Spreadsheet-friendly files

The same data, one row per item and one column per period, for spreadsheets.

- `data/wide/person_days_by_state.csv`: Person-days of work in each State or UT, one column per financial year (the latest year runs to 2026-04)

## Files

| Path | |
|---|---|
| `data/district_month/<financial year>.csv` | One row per district and month |

The [release](https://github.com/knowmoreindia/open-data/releases/tag/mgnrega) also has `all-copies-<financial year>.csv.gz`: 4,15,833 rows, every copy of each district's monthly row as the portal published it.

Columns are described in `codebook.csv` and `datapackage.json`.

## Quick start

```python
import pandas as pd

base = "https://raw.githubusercontent.com/knowmoreindia/open-data/main/mgnrega/data"
year = pd.read_csv(f"{base}/district_month/2026-2027.csv")
```

## Worth knowing

- Figures add up over the financial year. Each month's row is the year so far, not that month alone.
- The portal republishes a district's row many times as the month's figures come in. `district_month` keeps the copy with the most person-days. A few copies repeat a whole row with every count doubled; those are left out of `district_month` and kept in `all-copies`.
- The portal does not state the unit of the money columns.

## How to cite

Know More India, *MGNREGA*, version 2026-11-25, https://github.com/knowmoreindia/open-data/tree/main/mgnrega. Licensed CC BY 4.0.

```bibtex
@misc{knowmoreindia_mgnrega,
  author = {{Know More India}},
  title = {MGNREGA},
  year = {2026},
  version = {2026-11-25},
  howpublished = {\url{https://github.com/knowmoreindia/open-data/tree/main/mgnrega}}
}
```

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Credit: Know More India, from the Ministry of Rural Development (data.gov.in).
