````markdown
# Ovi Goal Tracker Board

A **Goal Tracking Board** for the [NHL LED Scoreboard](https://github.com/falkyre/nhl-led-scoreboard) that displays Alex Ovechkin's progress towards the all-time NHL goals record.

This board tracks Ovechkin's:
- Current career goals
- Current season goals and expected goals
- Career points
- Progress towards passing NHL goal-scoring legends:
  - Jaromir Jagr (767 goals)
  - Gordie Howe (802 goals)
  - Wayne Gretzky (895 goals)

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
- [Display Modes](#display-modes)
- [How It Works](#how-it-works)
- [Screenshots](#screenshots)

---

## Features

- Real-time goal tracking using NHL API
- Displays Ovechkin's career goal count prominently
- Automatically updates with latest game statistics
- Shows progress towards next milestone
- Dual display modes:
  - Season projection mode showing current season goals and projected total
  - Career points mode showing total NHL points
- Supports both 64x32 and 128x64 LED matrix displays
- Custom Ovechkin graphics for visual appeal

---

## Installation

1. Use the NHL Led Scoreboard's plugin manager python script to install:

   ```bash
   python plugins.py add https://github.com/tsmooth3/nls-plugin-ovi-goal-tracker.git
   ```

2. Add `ovi_goal_tracker_board` to your NHL-LED-Scoreboard's main configuration:

   ```bash
   nano config/config.json
   ```

   For example, to add it to the off day rotation:

   ```json
   "states": {
       "off_day": [
           "season_countdown",
           "ovi_goal_tracker_board",
           "team_summary",
           "scoreticker",
           "clock"
       ]
   }
   ```

   **Note:** You must restart the scoreboard for changes to take effect.

---

## Configuration

To configure the Ovi Goal Tracker board, copy the sample config to config.json and edit it:

```bash
cp config.sample.json config.json
nano config.json
```

**Note:** You must restart the scoreboard for changes to take effect.

### Config Fields

- `enabled` → Enable or disable the board (default: true)
- `ovigoals_alt` → Toggle between season projection mode (true) and career points mode (false)

---

## Display Modes

The board offers two display modes that can be toggled using the `ovigoals_alt` configuration setting:

### Season Projection Mode (`ovigoals_alt: true`)
- Shows current season goals in parentheses
- Displays projected goals for 82-game season (marked with *)
- Useful for tracking Ovechkin's current season pace

### Career Points Mode (`ovigoals_alt: false`)
- Shows "pts:" followed by career points total
- Provides context of Ovechkin's overall NHL impact

---

## How It Works

1. The board fetches real-time statistics from the NHL API for Alex Ovechkin (Player ID: 8471214)
2. It processes and displays:
   - Career goal total
   - Current season statistics (games played, goals)
   - Calculates goal-scoring pace and projects full season total
   - Tracks progress towards NHL records:
     - 3rd place (Jaromir Jagr - 767 goals)
     - 2nd place (Gordie Howe - 802 goals)
     - 1st place (Wayne Gretzky - 895 goals)
3. Display automatically updates to show:
   - Distance to next milestone when chasing records
   - "BEST )))" with goal differential when the record is broken
4. Updates every 15 seconds to ensure current statistics

---

## Installation

1. Use the NHL Led Scoreboard's plugin manager python script to install:

   ```bash
   python plugins.py add https://github.com/tsmooth3/nls-plugin-ovi-goal-tracker.git
   ```

2. Add `ovi_goal_tracker` to your NHL-LED-Scoreboard's main configuration:

   ```bash
   nano config/config.json
   ```

   For example, to add it to the off day rotation:

   ```json
   "states": {
       "off_day": [
           "season_countdown",
           "ovi_goal_tracker",
           "team_summary",
           "scoreticker",
           "clock"
       ]
   }
   ```

   **Note:** You must restart the scoreboard for changes to take effect.

## Display Examples

The board supports both 64x32 and 128x64 LED matrix displays:

### 64x32 Display Mode
- Simplified layout focusing on goal count
- Shows "OVECHKIN" and "GOALS" text
- Custom Ovechkin graphic

### 128x64 Display Mode
- Full-featured display with all statistics
- Shows current goal count, points/projections
- Progress towards NHL records
- Larger Ovechkin graphic

The board automatically detects your matrix size and adjusts the display accordingly.
````
