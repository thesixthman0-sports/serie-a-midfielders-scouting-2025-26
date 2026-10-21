# Serie A 2025-26: young midfielders, scouting profiles

Which Serie A midfielders born in 2002 or later stand out, and in what way? This project builds four playing profiles from public data, shortlists the leaders, and writes a short scouting note for eight players, each ending with a question for video.

*Written on 22 October 2026. No 2026-27 data are used.*

## What came out

| Profile | Leaders (born 2002+) |
|---|---|
| Creator (xA, key passes) | Martin Baturina (Como), Kenan Yildiz (Juventus), Jesús Rodriguez (Como) |
| Builder (xGBuildup, xGChain) | Petar Sucic (Inter), Francisco Conceição (Juventus) |
| Ball-winner (tackles won, interceptions) | Ebenezer Akinsanmiro (Pisa), Mandela Keita (Parma), Luca Lipani (Sassuolo) |
| Goal threat (npxG, shots) | Francisco Conceição, Nico Paz (Como), Jonathan Rowe (Bologna) |

- Most of the young creators and goal threats are wingers or attacking midfielders. Only Sucic, Akinsanmiro and Keita are central midfielders by role.
- Nico Paz is the most balanced profile (first for shots per 90, no metric below the 60th percentile).
- Four names on the lists are Como players, but this data cannot separate player quality from team style.
- Reliability check: shots, key passes, npxG, xGChain and xA are stable from season to season (rank correlation 0.74-0.88); xGBuildup is the least stable (0.67).

## Design (fixed before looking at results)

- Population: Serie A midfielders (FBref position starts with `MF`), at least 900 minutes in 2025-26 (153 players).
- Eight per-90 metrics, converted to percentiles within the population.
- Four profiles, two metrics each, score = mean percentile.
- Cards: the top two per profile among players born 2002 or later with at least 1,400 minutes, no player twice.
- Price and club are not used in selection. No market data are included.

## Data

Not redistributed here. Terms of each source should be checked before reuse.
- Understat via `understatapi` (xG, xA, shots, key passes, xGChain, xGBuildup). Season "2025" = 2025-26.
- Kaggle `hubertsidorowicz/football-players-stats-2025-2026` (FBref-based): age, birth year, position, minutes, tackles won, interceptions. This file has no xG, passing or progression columns despite its Kaggle description, which is why two sources are combined. Players are matched by name inside the same league (97.9% of Serie A players with 900+ minutes matched; a short alias list covers different spellings).

## Limitations

- No pressing, carrying or off-ball data, no video, no possession adjustment: defensive actions per 90 rise for teams that defend more.
- Positions come from FBref and group wingers and attacking midfielders with central midfielders.
- 900-1,400 minutes is a small sample.
- xGChain includes a player's own shots; Understat's key passes include set pieces.
- Selection ignores age curves, injuries, contract and price.

## How to run

Open `serie_a_midfielders_scouting.ipynb` in Google Colab, set `FOLDER` in the second code cell to a folder containing the Kaggle csv (`players_data-2025_2026.csv`), and run all cells. The first run downloads Understat data and caches it as csv in that folder.
