# Season Change

A computer graphics project built with **Python** and **PyOpenGL**. It draws a small city scene (buildings, trees, road) and animates it in three different seasons: **Summer**, **Rainy** and **Winter**.

Everything is drawn from scratch with basic graphics algorithms (midpoint line and midpoint circle) plus matrix transformations, rather than using ready-made shapes.

## Seasons

| # | Season | What you see |
|---|--------|--------------|
| 1 | **Summer** | Green leafy trees and a sun over the city. The scene is static. |
| 2 | **Rainy** | Rain streaks fall downward. The trees sway slightly (rotation of 0.9°). |
| 3 |  **Winter** | Trees are bare (trunks only, no leaves) and snow falls down the screen. |

## Graphics Concepts Used

- **Midpoint line algorithm** with zone conversion (zones 0 to 7), implemented in `mid_line.py` and used for buildings, windows, trunks and road lines
- **Midpoint circle algorithm**: the sun is drawn as 24 concentric circles
- **Translation matrix** (homogeneous coordinates) to move rain and snow along the negative y-axis
- **Rotation matrix** to give the tree foliage a small movement in the rainy season
- **Particle animation:** 1,000 randomly placed rain or snow particles that wrap back to the top when they leave the screen
- **Orthographic projection** (1000 × 1000 coordinate space) with double buffering via GLUT

## Project Structure

```
Season-Change/
├── season change.py   # Main program: scene, seasons, animation loop
├── mid_line.py        # Midpoint line drawing helper (drawLine)
└── README.md
```

## Requirements

- Python 3.x
- [PyOpenGL](https://pypi.org/project/PyOpenGL/) and PyOpenGL_accelerate
- NumPy
- GLUT (freeglut) available on your system

## Installation

### Option 1: pip (simplest)

```bash
pip install PyOpenGL PyOpenGL_accelerate numpy
```

### Option 2: Windows wheel files

1. Go to [Python Extension Packages for Windows (Christoph Gohlke)](https://www.lfd.uci.edu/~gohlke/pythonlibs/) and download the wheels that match your Python version:
   - `PyOpenGL-3.1.x-cp3x-cp3x-win_amd64.whl`
   - `PyOpenGL_accelerate-3.1.x-cp3x-cp3x-win_amd64.whl`

   Replace `3x` with your Python version, for example `cp36` for Python 3.6 or `cp39` for Python 3.9.

2. Open the terminal in PyCharm or VS Code and install them:
   ```bash
   pip install PyOpenGL-3.1.x-cp3x-cp3x-win_amd64.whl
   pip install PyOpenGL_accelerate-3.1.x-cp3x-cp3x-win_amd64.whl
   pip install numpy
   ```

> If you see a GLUT error such as `NullFunctionPointerError` when starting the program, install **freeglut** (the Windows wheels from the link above usually include it).

## Usage

1. Clone the repository
   ```bash
   git clone https://github.com/mdshakibulalam/Season-Change.git
   cd Season-Change
   ```

2. Run the program (the file name contains a space, so keep the quotes)
   ```bash
   python "season change.py"
   ```

3. When prompted in the terminal, choose a season:
   ```
   1) Summer  2) Rainy  3) Winter
   ```
   Type `1`, `2` or `3` and press Enter. An OpenGL window opens with the animation.

To switch seasons, close the window and run the program again.



