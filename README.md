# US school district weather-closing rules

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23931214.svg)](https://doi.org/10.5281/zenodo.23931214)

Published rules that US school districts use to decide whether to close or delay school for snow, ice and cold: wind chill and air temperature thresholds, snow criteria, when they check the forecast, when they decide, and what they do. Every row links its source.

- **108 districts in 45 states**, from Alaska, Washington and Maine to Georgia and Texas
- **One file:** [`school-closing-rules.csv`](school-closing-rules.csv), UTF-8, one row per district
- **Every source checked:** 3 or 4 November 2026
- **Licence:** [CC BY 4.0](LICENSE)
- **DOI:** [10.5281/zenodo.23931214](https://doi.org/10.5281/zenodo.23931214) (always the latest version, archived on Zenodo)
- **Web page with the table and method:** https://calculatesnowday.com/school-closing-rules

Maintained by Muhammad Shakeel at [CalculateSnowDay](https://calculatesnowday.com), a free snow day calculator built on the National Weather Service forecast.

## What the data shows

- Most published cold rules sit between **-20°F and -35°F wind chill**: 22 of the 37 wind chill thresholds fall in that band, and the median is -20°F. The mildest is 10°F (West Virginia) and the coldest -40°F (Iowa and Minnesota).
- **Southern districts rarely publish a temperature.** Only 5 of the 29 districts from the South, the mid-Atlantic and the southern Plains name one; most publish when they check the roads and when they decide instead.
- Decisions come early: of the 68 districts that give a morning deadline, 65 aim to decide by 6 am.
- 64 of the 108 rules mention a delay or late start, and 19 name an e-learning, virtual or other remote day as an option instead of a full closure.
- Few districts publish a snow amount. Most judge roads, ice and timing instead.

## Columns

| Column | Meaning |
|---|---|
| `district` | School district name |
| `state` | Two-letter state code |
| `wind_chill_f` | Wind chill threshold in °F (negative below zero). Blank if the source gives none. For a range, the milder end. |
| `air_temp_f` | Air temperature threshold in °F. Blank if the source gives none. |
| `snow_in` | Snow criterion as written, for example "5 to 10 in on the ground". Blank if none. |
| `check_time` | When the district checks the forecast or the roads |
| `decision_by` | When the decision is usually made |
| `action` | What the rule leads to: close, delay, e-learning or remote day |
| `rule` | The rule in plain words, including any range |
| `source_name` | District website, board policy or news outlet |
| `source_date` | Month of the source as YYYY-MM, blank if the page is undated |
| `source_url` | Link to the source |
| `date_checked` | Date the source was last read |

The file starts with a UTF-8 byte order mark so Excel shows the °F sign correctly. Most CSV readers handle it automatically; in Python use `encoding="utf-8-sig"`.

```python
import pandas as pd
df = pd.read_csv("school-closing-rules.csv", encoding="utf-8-sig")
df["wind_chill_f"].describe()
```

## How it was collected

- **What counts.** A rule is included only if a district page, board policy, or a dated news story quoting the district states something concrete: a temperature or wind chill, a snow amount, a check or decision time, or the action taken. Pages that only say "many factors" are left out, and so are one-off closing announcements.
- **Checked at the source.** Every row was read on its source page on the date in `date_checked`. Numbers are only what the source states.
- **Sources differ.** District pages are the best source. News quotes from a superintendent are guidelines, not formal policy, and older stories may describe rules that have since changed.
- **Not a complete list.** These are districts that publish a rule. Northern districts publish temperature thresholds far more often than southern ones, and many districts publish no rule at all.

Districts change their rules. Always check your own district before relying on a row.

## How to cite

> Shakeel, M. (2026). *US school district weather-closing rules* (Version 2026-11-03.2) [Data set]. CalculateSnowDay. https://doi.org/10.5281/zenodo.23931214

GitHub's "Cite this repository" button uses [`CITATION.cff`](CITATION.cff).

## Corrections and additions

If your district's rule is missing or out of date, open an issue with a link to the district's page, or email hello@calculatesnowday.com. The data is rechecked every school year; see [`CHANGELOG.md`](CHANGELOG.md).
