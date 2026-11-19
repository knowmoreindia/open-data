# IAS officers

Every officer of the Indian Administrative Service, from the Department of Personnel and Training's civil lists (2020 to 2026) and its Supremo officer records.

## Files

Each table is in `data/` as CSV. Each [release](https://github.com/knowmoreindia/ias-officers-data/releases/latest) also has `ias.sqlite` with every table, the tables as Parquet, and `officers.jsonl.gz` with one record per officer.

| Table | |
|---|---|
| `officers` | One row per officer, serving and retired |
| `identity_numbers` | Every identity number an officer has held |
| `civil_list` | Every officer in every yearly civil list |
| `seniority` | All-India seniority lists of each year |
| `education` | Degrees, with university, subject and division |
| `postings` | Every post held, with dates |
| `trainings` | In-service, domestic, foreign and mid-career training |
| `awards` | Awards and publications |
| `cadre_strength` | Authorised and actual strength of each cadre, each year |
| `cadre_reviews` | Cadre reviews and their notification dates |
| `retirements` | Officers due to retire, by cadre and year |
| `exam_intake` | Officers appointed through the civil services examination, by batch |
| `editions` | Each yearly civil list |

Columns are described in `codebook.csv`.

## Quick start

```python
import pandas as pd

officers = pd.read_csv("https://raw.githubusercontent.com/knowmoreindia/ias-officers-data/main/data/officers.csv")
postings = pd.read_csv("https://raw.githubusercontent.com/knowmoreindia/ias-officers-data/main/data/postings.csv")
```

```sql
-- sqlite3 ias.sqlite
SELECT name, cadre, allotment_year, posting FROM current_officers WHERE cadre = 'UP';
```

## Joining

Every table joins on `officer_key`. It stays the same for an officer across years, even when their identity number changes.

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Credit: Know More India, from DoPT.
