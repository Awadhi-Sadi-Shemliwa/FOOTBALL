# FOOTBALL — Expected Goals Analysis

A portfolio project building and evaluating an expected-goals model using shots from the 2015/16 Premier League season. The analysis explores shot location and context, evaluates probability quality, and compares the model with StatsBomb’s xG values.

## Project files

- [Analysis notebook](football_expected_goals_analysis.ipynb)
- [Interactive walkthrough](https://awadhi-sadi-shemliwa.github.io/FOOTBALL/football_expected_goals_animation.html)
- [Project video: What Repeats?](https://awadhi-sadi-shemliwa.github.io/FOOTBALL/football-what-repeats_hq.html)
- [MP4 video file](football-what-repeats_hq.mp4)
- [Original project notes](football_expected_goals_README.md)

## Headline result

The project reports a log loss of about 0.283 on the final 76 matches for its best in-house model, compared with about 0.273 for StatsBomb’s benchmark. It also examines whether finishing above expected goals persists across the season.

## Data and scope

The shot data comes from StatsBomb Open Data. This analysis covers one league season and is not a general evaluation of player ability.

## Reproduction note

This repository includes the supplied notebook, HTML walkthrough, project video, and project notes. Reproducing the analysis may also require the data-preparation script, match and shot data, dependencies, and generated results and figures.
