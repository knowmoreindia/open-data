# Aviation data

Monthly air traffic in India by airport, State, airline and route, from the Airports Authority of India (AAI) and the Directorate General of Civil Aviation (DGCA), as tidy CSV files.

**September 2026:** Indian airports handled 3.01 crore passenger arrivals and departures (AAI). Indian airlines flew 118.23 lakh domestic passengers, IndiGo 65.4% of them (DGCA).

## Quick start

```python
import pandas as pd

base = "https://raw.githubusercontent.com/knowmoreindia/aviation-data/main/data"
airports = pd.read_csv(f"{base}/aai/airport-traffic-monthly.csv")
report = pd.read_csv(f"{base}/dgca/report-card.csv")
routes = pd.read_csv(f"{base}/dgca/routes-domestic.csv")
```

Airports are keyed by `code` (IATA, or ICAO where there is none) and airlines by `id` like `indigo`, the same in every file. `airports.csv` and `airlines.csv` hold the details.

## Files

| Path | What's in it |
|---|---|
| `data/airports.csv` | Every airport any source names: code, IATA, ICAO, name, city, State, UDAN |
| `data/cities.csv` | Cities with more than one airport that DGCA sometimes prints without naming the airport (Mumbai, Goa) |
| `data/airport-names.csv` | Each name AAI and DGCA print for an airport, with the months it applies to |
| `data/airlines.csv` | Every airline and DGCA group row: kind, IATA code, when it started and stopped, renamings, mergers, head office |
| `data/airline-names.csv` | Each name DGCA prints for an airline |
| `data/aai/airport-traffic-monthly.csv` | A row per airport per month: aircraft movements, passengers and freight (tonnes), each international, domestic, transit where printed, and total |
| `data/aai/state-traffic-monthly.csv` | The same three measures by State and UT, for the month and April to date |
| `data/aai/category-monthly.csv` | Totals by AAI airport category, with the same month a year earlier and year to date |
| `data/aai/region-monthly.csv` | Totals by AAI region, in the same form |
| `data/aai/printed-lines-monthly.csv` | Each table's printed grand total, and groups AAI prints as one line without listing airports |
| `data/aai/revisions.csv` | Airport figures that the next year's release printed differently |
| `data/aai/annual-check.csv` | Monthly airport passengers summed over each April to March, against AAI's own annual total |
| `data/dgca/report-card.csv` | DGCA's monthly domestic Traffic Report in long form: market share, passengers, load factor, on-time performance, cancellations, delays, complaints, passenger charter compensation and route dispersal |
| `data/dgca/report-card-revisions.csv` | Earlier printings of report card figures that a later issue changed |
| `data/dgca/report-issues.csv` | Each Traffic Report issue read: file, revision, sections, and the airports its on-time performance covers |
| `data/dgca/operating-stats.csv` | DGCA's monthly traffic and operating statistics (ICAO Form A) by airline, service and sector: departures, hours, passengers, passenger-km, seat-km, load factors, freight, mail, tonne-km |
| `data/dgca/routes-domestic.csv` | Passengers, freight and mail between each pair of Indian cities, by month |
| `data/dgca/routes-international-airlines.csv` | International passengers and freight to and from India by airline, by quarter |
| `data/dgca/routes-international-airlines-monthly.csv` | The same by month |
| `data/dgca/routes-international-countries.csv` | International passengers and freight by country, by quarter |
| `data/dgca/routes-international-city-pairs.csv` | International passengers and freight by city pair, by quarter |
| `data/airports/operators.csv` | Who runs each airport that AAI does not run alone: operator, group, arrangement, dates, term, AAI's stake, what it pays AAI, each with sources |
| `data/airports/ppp-events.csv` | Every dated step of each leasing or concession round, 1999 to 2026 |
| `data/airports/ppp-bids.csv` | Every bid in the 2019 round for six AAI airports |
| `data/ministry/values.csv` | Ministry of Civil Aviation tables from Rajya Sabha answers on data.gov.in: AAI and operator profit and loss by airport, AAI income, capacity, user development fees, airports with no flights, operators and AAI stakes |
| `data/ministry/tables.csv` | Each data.gov.in table read, with its link |
| `data/parliament/values.csv` | Figures from Lok Sabha and Rajya Sabha answers and data.gov.in: bird, animal and laser strikes, accidents, technical faults, DGCA enforcement, bomb threats, pilot licences, drones, Digi Yatra and AAI airports' ten-year losses |
| `data/parliament/sources.csv` | Each answer and table behind parliament/values.csv |
| `data/aaib/reports.csv` | Every investigation report on the Aircraft Accident Investigation Bureau's site, with date, kind, operator, aircraft, registration and place |
| `data/dgca/fleet-aircraft.csv` | Every aircraft on DGCA's scheduled and non-scheduled operator lists: operator, model, seats, registration |
| `data/dgca/fleet-operators.csv` | The operators on those lists, with permit and validity (contact details left out) |
| `data/dgca/flight-schools.csv` | DGCA-approved flight schools: bases, aircraft, and grade in DGCA's ranking |
| `data/gaps.csv` | Every month, issue or series with no figure, and why |
| `data/notes.csv` | Printed errors, revisions, totals that do not add up, and other notes the sources print or the reading recorded |
| `data/sources.csv` | Every file read: link and SHA-256 |
| `codebook.csv` | Every column and what it counts (also as `datapackage.json`) |

## Coverage

| Source | Files | First | Latest | Rows |
|---|---|---|---|---|
| AAI airports | `aai/airport-traffic-monthly.csv` | 2014-01 | 2026-09 | 16,105 |
| AAI States and UTs | `aai/state-traffic-monthly.csv` | 2024-05 | 2026-09 | 2,030 |
| AAI airport categories | `aai/category-monthly.csv` | 2014-01 | 2026-09 | 10,325 |
| AAI regions | `aai/region-monthly.csv` | 2014-01 | 2026-09 | 8,046 |
| DGCA Traffic Report | `dgca/report-card.csv` | 2014-06 | 2026-09 | 37,523 |
| DGCA operating statistics | `dgca/operating-stats.csv` | 2009-01 | 2026-10 | 5,646 |
| DGCA domestic routes | `dgca/routes-domestic.csv` | 2015-04 | 2026-10 | 69,467 |
| DGCA international, quarterly | `dgca/routes-international-airlines.csv`, `dgca/routes-international-countries.csv`, `dgca/routes-international-city-pairs.csv` | 2015-Q1 | 2026-Q2 | 22,394 |
| DGCA international by month | `dgca/routes-international-airlines-monthly.csv` | 2015-01 | 2026-06 | 11,154 |

## Updates

A weekly job runs on Mondays, reads any new AAI and DGCA releases, including DGCA's operator and flight school lists, and rebuilds these files. The Ministry and Parliament tables are read by hand when new answers appear. AAI posts a month's figures about a month after it ends. DGCA's Traffic Report follows 3 to 4 weeks after the month, and the quarterly international tables about 7 weeks after the quarter.

Later releases can revise earlier months. The AAI files keep each month's own release and list later figures in `data/aai/revisions.csv`. The report card keeps the latest printing and lists earlier ones in `data/dgca/report-card-revisions.csv`. Either way a past row in these files can change from one update to the next. `CHANGELOG.md` lists each source version read.

## Worth knowing

- AAI counts a domestic passenger at both the airport they leave and the one they land at, so its passenger totals are about twice DGCA's airline figures.
- DGCA's on-time performance covers only 4 to 10 big airports, listed for each issue in `report-issues.csv`.
- Airline names are unified through one registry (`airlines.csv`). The name each source printed is kept beside the id, and combined rows DGCA prints, such as Air India Group, keep their own id.
- City names in the route files are kept as DGCA prints them, with the airport code beside each Indian city.
- A blank cell means the source printed nothing. Nothing is estimated or zero-filled. Missing months are listed in `gaps.csv`.
- Figures that contradict each other on the same page are kept as printed and listed in `notes.csv`.
- Report card passengers are in lakh, as DGCA prints them. Freight and mail are in tonnes. Decimals are rounded to 12 significant digits to drop floating-point noise.

## Licence

The compiled tables are [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Please credit "Know More India, from AAI and DGCA data".

The figures keep their publishers' terms. DGCA's website policy allows its material to be reproduced free of charge, accurately, with the source prominently acknowledged. AAI's reuse terms are not stated. data.gov.in tables are under the Government Open Data License - India. sansad.in and aaib.gov.in state no reuse terms.
