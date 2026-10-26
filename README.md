# Forecast Report Card

**Which weather forecast is actually right for your town?**

Live site: https://jakeking-dev.github.io/forecast-report-card/

Look up any town and see seven major forecast models (ECMWF, GFS, ICON, GEM,
UK Met Office, JMA, Météo-France) graded A to F on how well they predicted
the daily high, low and rain over the last 30 days.

## How the grading works

- For each of the last 30 full days, each model's forecast made 1, 2 and 3 days
  ahead is compared with what happened.
- Every model is graded against the same reference, Open-Meteo's historical
  weather record for that spot. Grading a model against its own later runs would
  let it mark its own homework.
- The letter grade is the average miss on the high and low one day ahead:
  A under 2°F, B under 3°F, C under 4°F, D under 5°F, F at 5°F or more.
- Rain is scored as the share of days a model correctly called wet (1 mm or
  more) or dry.

**Limits:** the reference is a model-based estimate for a grid square, not a
backyard thermometer, and is built partly from ECMWF data, which may slightly
favor that model. Thirty days is one season, not a permanent verdict.

## Evolution Lab

Below the grades, a genetic algorithm evolves 48 recipes for blending the
models over 60 generations. Each recipe gives every model a share of trust
and adds a correction to the high and low. Recipes are scored only on the
first two-thirds of the month (practice); the last third stays sealed as an
exam. The champion counts as trusted only if it beats the best single model
on the exam and the 90% range of its improvement (by resampling exam days)
stays above zero. The first run for each town and day is deterministic and is
the official one; reruns are labeled as reruns.

## Running it

It's one static HTML file with no build step and no server. Open
`index.html` in a browser.

## Data

Weather data by [Open-Meteo.com](https://open-meteo.com/), licensed
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Grades are computed
from that data in your browser.

## Sponsorship

Interested in sponsoring the Forecast Report Card? Email jacobnotjoking@gmail.com.

Made by Jacob King.
