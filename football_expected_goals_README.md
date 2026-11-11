# Expected goals: how good was that chance?

An expected-goals (xG) model built from every shot of the 2015/16 Premier League season, compared against StatsBomb's commercial xG, and used to ask what a club should pay for when it buys a goalscorer.

**Business question.** How much of a forward's goal total is repeatable?

**Answer in one paragraph.** A logistic regression with distance, angle, body part and defender positions reaches a log loss of 0.283 on the final 76 matches, against 0.330 for a constant baseline and 0.273 for StatsBomb's own model. Across 56 players, scoring more than expected in the first half of the season did not predict doing so in the second half (r = −0.08), while the quality of chances a player gets did persist (r = 0.66). Buy chance volume and quality, not a finishing streak.

![Shot map](figures/fig1_shot_map.png)

## What is in this repository

| Path | Contents |
|---|---|
| `src/get_data.py` | Reads 380 StatsBomb match files and writes `data/shots.csv` (one row per shot) |
| `src/analysis.py` | The whole analysis with `# %%` cells |
| `analysis.ipynb` | The same analysis as an executed notebook |
| `data/shots.csv`, `data/matches.csv` | 9,908 shots and 380 match results extracted from StatsBomb Open Data |
| `figures/`, `results/metrics.json` | Figures and every number quoted in the paper |
| `paper/paper.md` | Write-up in research-paper format with references |
| `animation.html` | Step-through explanation of the project |

## Run it

```bash
pip install -r requirements.txt
python src/get_data.py      # optional: data/shots.csv is already included (reads about 1.2 GB over the network)
python src/analysis.py
```

## Data and credit

Data provided by **StatsBomb** through [StatsBomb Open Data](https://github.com/statsbomb/open-data), free for public research and analysis. Their terms ask that StatsBomb is credited as the data source in anything published from it.

## Method in brief

1. **Clean**: flags that are 70 to 99.9% empty are "false by design" and filled accordingly; 91 penalties set aside; coordinates turned into distance and angle; defender and goalkeeper positions summarised.
2. **Explore**: shot map, conversion by distance, by defenders in the way, by body part.
3. **Split by date**: first 304 matches for training, final 76 for testing; a match is never on both sides.
4. **Model**: baseline, two-feature logistic, full logistic, gradient boosting, StatsBomb benchmark.
5. **Evaluate**: log loss, Brier score, calibration (accuracy is meaningless when 91% of shots miss).
6. **Decide**: out-of-fold season xG per player and team; does over-performance persist between halves of the season?
