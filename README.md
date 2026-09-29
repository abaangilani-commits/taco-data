# US taco spots per capita, 2026

Open data on where tacos actually are in the United States: **52,007 taquerias, taco shops,
taco trucks, stands and birrierias**, counted against US Census population estimates for
107 cities and all 50 states plus DC.

Built because nobody had counted. Restaurant-count datasets stop at "Mexican restaurant",
which lumps a Tex-Mex sit-down in with a trompo on a sidewalk, and chain-location data
ignores the independents that make up 74% of the total.

## What's here

| File | Rows | What it covers |
|---|---|---|
| [`data/taco-spots-by-city.csv`](data/taco-spots-by-city.csv) | 107 | Cities with 100,000+ residents and 50+ taco spots |
| [`data/taco-spots-by-state.csv`](data/taco-spots-by-state.csv) | 51 | Every state and DC |

### City columns

`city`, `state`, `population_2025`, `taco_spots`, `taco_spots_per_100k`,
`independent_spots`, `independent_pct`, `independents_per_100k`, `taquerias`,
`birrierias`, `trucks_and_stands`

### State columns

`state`, `population_2025`, `taco_spots`, `taco_spots_per_100k`, `independent_pct`,
`independents_per_100k`, `taco_bell_pct`, `largest_chain`, `largest_regional_chain`

## Some findings

**The Rio Grande Valley is the densest taco region in America.** McAllen, Texas has 87.6
taco spots per 100,000 residents. Edinburg has 84.9, Brownsville 77.2. The top five
densest cities in the country are all in Texas.

**Among big cities, Las Vegas leads at 55.5 per 100,000** — ahead of Austin (51.5),
Houston (50.5) and San Antonio (49.6).

**New York City is last among large cities, at 6.7 per 100,000.** Philadelphia is second
last at 7.4. This is partly real and partly a measurement artefact: street vendors and
pop-ups are the hardest thing to count, and they weigh most heavily in exactly those
cities. Treat the number as a floor.

**Texas leads the states at 31.5 per 100,000; Maine is last at 4.8.**

**Chain share varies enormously.** Taco Bell is 8% of Texas taco spots and 32% of Maine's.
Nationally, 17% of everything on this list is a Taco Bell.

**"Taqueria Jalisco" is the most common taco business name in America** — 80 of them
across 20 states, followed by "El Taco Loco" (62 in 23 states).

## How it was built

Venue records come from two open map sources, merged and deduplicated:

- [OpenStreetMap](https://www.openstreetmap.org) (ODbL)
- [Overture Maps Places](https://overturemaps.org), 2026-08-19.0 release (CDLA-Permissive-2.0)

A place is counted when its name references tacos, taquerias or birria, or when it is
categorised as a taco restaurant. Low-confidence and closed records are dropped. Chain
locations are matched within 300 m and name-matched within 120 m to avoid double counting
the same restaurant appearing in both sources. Burrito-first chains such as Chipotle and
Qdoba are excluded, because a burrito chain is not a taco spot.

Population is [US Census Bureau Population Estimates Program, Vintage 2025](https://www.census.gov/programs-surveys/popest.html)
(July 1 2025 estimates), which is US Government work and in the public domain.

## Caveats worth reading before you cite this

**These are floors, not a census.** A taco spot missing from both map sources is not
counted. Street vendors, pop-ups and unlicensed stands are the most under-counted, which
biases the numbers downward hardest in cities with large sidewalk-vendor scenes — Los
Angeles and New York especially.

**Cities are address cities.** A venue counts toward whatever city its address names,
which can include unincorporated areas next door. That is why only cities of 100,000+
residents with 50+ spots are ranked; below that, the noise swamps the signal.

**Chain detection is name-based** and will miss a franchise trading under a local name.

## Licence

The data is published under the [Open Database License 1.0](https://opendatacommons.org/licenses/odbl/1-0/)
(full text in [`LICENSE.txt`](LICENSE.txt)), because it derives from OpenStreetMap, whose
share-alike terms are the strictest of the inputs.

In practice: use the numbers, charts and rankings freely, with credit. If you publish a
modified version of the database itself, that stays under ODbL.

Please credit **Tacos Near You** and link to https://tacosnearyou.com/taco-report/

## Source

The full report, with charts and a state map, is at
https://tacosnearyou.com/taco-report/ — where the underlying directory of 52,000 taco
spots also lives.

Questions, corrections, or a city that looks wrong? Open an issue.
