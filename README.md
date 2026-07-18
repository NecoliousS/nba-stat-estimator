# 🏀 NBA Stat Estimator

A Python-based NBA analytics tool that:
- Projects player stats over a full season
- Calculates performance ratings
- Assigns player tiers (Superstar → Bench)
- Generates scouting-style insights
- Compares players head-to-head

## Features
- PPG, RPG, APG, SPG, FG%, 3PT tracking
- Season projection system
- Input validation
- Player comparison tool
- AI-style player insights

## How to Run
```bash
python main.py
# NBA Stat Estimator

A fantasy basketball tool that takes current-season per-game stats and projects them across a full 82-game season. Includes player ranking, tier system, and head-to-head comparison.

## Live Demo

https://necoliouss.github.io/nba-stat-estimator/

## What It Does

- Input any player's current stats (games played, MPG, PPG, RPG, APG, SPG, FG%, 3PM/3PA)
- Automatically scales stats to a full 82-game season
- Calculates an overall rating score and assigns a tier (Superstar, Star, Starter, Role Player, Bench)
- Generates player analysis based on stat thresholds
- Roster management with add/remove
- Head-to-head stat comparison with visual bar charts
- Toggle between per-game and season-total views

## Tech Stack

- Vanilla HTML/CSS/JS (single file)
- No external dependencies
- CSS custom properties for theming
- Grid and flexbox for layout

## What I Learned

The projection math seems simple (multiply by games ratio) until you realize NBA stats don't scale linearly. A player averaging 35 MPG over 10 games isn't necessarily playing 35 MPG over 82. I added a hard cap at 48 minutes and let the math handle the rest. The scoring algorithm was trial and error — I weighted assists and steals higher than points because playmaking and defense are harder to find in fantasy, but I had to dial back the FG% multiplier because it was overrating centers who don't shoot threes.

The comparison view was the most complex part. I needed bars that fill proportionally between two values, but CSS doesn't have a "fill from center" property. I solved it by using two separate bars with `direction: rtl` on the right side, then flipping the fill back with `direction: ltr` on the inner element. It looks clean but the code is not obvious at first glance.

Validation was another headache. I kept the checks simple (games played can't exceed season games, MPG max 48, FG% max 100) but the error messages needed to show and hide without cluttering the UI. Toggling a `.show` class on validation divs kept the markup clean.

## Features

- 5-tier ranking system with color-coded badges
- Projected season totals (points, rebounds, assists, steals, minutes, threes)
- Player analysis generator based on stat thresholds
- Side-by-side comparison with proportional bar visualization
- Responsive layout that stacks on mobile
- No build step, no dependencies, loads instantly
