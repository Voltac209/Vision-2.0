# Vision 2.0

Vision 2.0 is a Python simulation project that combines:

- Computer vision (OpenCV) for color/shape detection
- Path planning (BFS on a directed graph)
- Robot simulation (PyBullet + Gym custom environment)

The bot navigates a 9x9 arena, detects target shape-color combinations, and moves clockwise to complete the task by returning to the home zone.

## Features

- Randomized arena generation with colored base paths and shape placement
- ArUco-based bot localization from camera feed
- Color segmentation + contour approximation for shape extraction
- Directed-graph traversal using BFS to select shortest valid path
- Movement control using heading alignment + forward motion loop

## Requirements

- Python 3.9+ recommended
- Pip
- (Windows) Microsoft C++ Build Tools may be required for some packages

## Installation

1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
pip install -e vision-arena
```

## Run

```bash
python vision.py
```

## How It Works

1. The environment loads a randomized arena in PyBullet.
2. The bot spawn point is one of the outer arrow cells.
3. A target code is generated (`TR`, `SR`, `CR`, `TY`, `SY`, `CY`).
4. Vision pipeline extracts all matching target cells from the arena image.
5. BFS computes candidate paths; shortest valid path is selected.
6. Bot aligns and moves cell-by-cell to the target.
7. After completing the clockwise cycle, the bot returns to home (`40`) and exits.

## License

MIT License (see `LICENSE`).
