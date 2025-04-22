# Fruit Ninja Bot Analysis

### CS2203 AI Project – IIT Patna

- **Khaled Hussain Mohammed – 2301CS24**  
- **Srichetan Reddy – 2301CS54**  
- **G. Praneeth Reddy – 2301CS36**  
- **B. Rahen – 2301CS37**  
- **Koushik – 2302CS02**

---

## Overview

This script is a bot designed to automate gameplay for what appears to be Fruit Ninja or a similar fruit-slicing game. The bot uses computer vision techniques to detect fruits and bombs on the screen, then executes mouse movements to slice fruits while avoiding bombs.

---

## Key Components

### Technical Foundation

- Uses Python with libraries like OpenCV, MSS (screen capture), NumPy, and Win32API  
- Captures game screen in a specific region of the display  
- Processes images to detect objects based on color ranges  
- Can record gameplay videos when run with the 'save' parameter

### Game Interaction

- Performs "swipes" by generating mouse movements to slice detected fruits  
- Prioritizes fruits closest to the screen edges (likely to fall out of view soon)  
- Implements bomb avoidance by predicting bomb trajectories  
- Uses a caching system to avoid slicing the same area repeatedly

### Object Detection

- Identifies fruits and bombs through color masking and contour detection  
- Uses different color boundaries for various fruit types  
- Calculates precise object centers for accurate slicing

### Safety Features

- Checks if swiping paths intersect with bombs or their predicted trajectories  
- Tries different slicing angles when bombs block the direct path  
- Includes safeguards to prevent cursor movement outside game boundaries

---

## Technical Implementation Details

### Screen Handling

- Game resolution is set to 1109x742 pixels  
- Places game in the top-right corner of the screen  
- Uses a multi-threaded approach to handle swipes without blocking main detection loop

### Bomb Avoidance Algorithm

- Maintains lists of bombs from current and previous frames  
- Predicts bomb trajectories based on previous positions  
- Enforces minimum safe distance (58 pixels) from bombs  
- Tests multiple slicing angles when direct paths are unsafe

### Performance Optimization

- Caches recently swiped areas to avoid redundant actions  
- Sorts fruits by priority (those closest to falling out of view)  
- Uses threading to separate detection from mouse movement execution

---

## Use Cases

- Automation of gameplay for high scores  
- Testing game mechanics and performance  
- Creating demonstration videos with the recording functionality

---

## Limitations

- Relies on specific screen coordinates and color values  
- May require recalibration for different display settings  
- Performance depends on processing power and screen capture speed

This bot demonstrates sophisticated computer vision techniques for real-time game automation, balancing speed and accuracy to maximize fruit slicing while avoiding bombs.

---

## Key Code Sections Explained

### Screen Capture Setup

```python
gameScreen = {'top': 25, 'left': screenWidth - width, 'width': width, 'height': height}
