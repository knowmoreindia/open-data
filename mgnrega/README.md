# MGNREGA

What the rural jobs scheme did in every district, every month since April 2018: person-days of work, households and individuals who worked, wages and spending, works started and finished, job cards, and work done by women, Scheduled Castes and Scheduled Tribes.

743 districts. Latest month: 2026-04.

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

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Credit: Know More India, from the Ministry of Rural Development (data.gov.in).
