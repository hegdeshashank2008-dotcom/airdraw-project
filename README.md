# AirDraw — Hand Gesture Controlled Canvas
# AUTHOR: SHASHANK HEGDE
# INSTITUTE: MOODLAKATTE INSTITUTE OF TECHNOLOGY, KUNDAPUARA, INDIA

Draw in the air using nothing but your webcam and your hand. AirDraw uses real-time hand tracking to turn your index finger into a paintbrush — no mouse, no stylus, no touchscreen.

![Python](https://img.shields.io/badge/Python-3.9%20--%203.12-blue)
![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-green)
![MediaPipe](https://img.shields.io/badge/MediaPipe-Hand%20Tracking-orange)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

  Features

- **Real-time hand tracking** powered by MediaPipe's HandLandmarker
- **Draw with your index finger** — raise it alone to start drawing
- **Gesture-based tool selection** — raise index + middle finger to hover and click toolbar buttons
- **7 colors**: Blue, Green, Red, Yellow, Purple, Cyan, White
- **Eraser** and one-tap **Clear canvas**
- **Undo / Redo** stroke history
- **Save your drawing** as a PNG, any time
- **Adjustable brush size**
- **Live hand-skeleton visualization** overlaid on the video feed
- Full keyboard shortcuts as a backup to gestures
- On-screen FPS and mode HUD

---

##  How It Works

Every video frame, MediaPipe detects 21 landmark points on your hand. AirDraw watches two things:

1. **Which fingers are extended** → decides the current *mode*
2. **Where your index fingertip is** → decides *where* to draw or click

| Gesture | Mode | What happens |
|---|---|---|
| Index finger only | **DRAW** | Fingertip position is smoothed and connected frame-to-frame into a continuous line on the canvas |
| Index + middle finger | **SELECT** | Fingertip acts like a cursor — hover over a toolbar button for ~0.9s to "click" it |
| Anything else | **IDLE** | No drawing, no selecting |

### Choosing a color
Enter SELECT mode → hover over a color swatch → hold ~0.9s until the progress bar fills → that color becomes active. Switch back to DRAW mode to use it.

### Erasing
- **Spot erase**: SELECT mode → hover "Eraser" → draw over what you want to remove (uses a larger brush, paints "nothing" instead of color)
- **Wipe everything**: SELECT mode → hover "Clear"

---

##  Getting Started

### Python version requirement

MediaPipe currently only publishes wheels for **Python 3.9 – 3.12**. If your system uses Python 3.13/3.14, install Python 3.12 separately (it can coexist with your existing version) and use it just for this project — see setup below.

### Installation

```bash
git clone https://github.com/<your-username>/airdraw.git
cd airdraw
pip install -r requirements.txt
python airdraw.py
```

If you're on Windows with a newer Python that MediaPipe doesn't support yet, use the included setup scripts instead, which create an isolated virtual environment automatically:

```powershell
# Windows
.\setup_windows.bat
.\venv\Scripts\Activate.ps1
python airdraw.py
```

```bash
# macOS / Linux
chmod +x setup_unix.sh
./setup_unix.sh
source venv/bin/activate
python airdraw.py
```

> **First run:** AirDraw automatically downloads a small (~7 MB) hand-tracking model file into the project folder. This requires internet access once; after that it's cached and works offline.

---

##  Controls

### Gestures
| Gesture | Action |
|---|---|
| Index finger up | Draw |
|  Index + middle up | Select / hover toolbar |
| Hold ~0.9s on a button | Click it |

### Keyboard
| Key | Action |
|---|---|
| `1`–`7` | Pick a color (Blue, Green, Red, Yellow, Purple, Cyan, White) |
| `E` | Eraser |
| `D` | Back to draw mode |
| `C` | Clear canvas |
| `U` / `R` | Undo / Redo |
| `S` | Save canvas as PNG |
| `+` / `-` | Increase / decrease brush size |
| `Q` | Quit |

---

##  Tech Stack

- **[Python](https://www.python.org/)** — core language
- **[OpenCV](https://opencv.org/)** — video capture, drawing, and rendering
- **[MediaPipe](https://ai.google.dev/edge/mediapipe)** — real-time hand landmark detection (Tasks API)
- **[NumPy](https://numpy.org/)** — canvas and array operations

---

##  Project Structure

```
airdraw/
├── airdraw.py              
├── requirements.txt        
├── setup_windows.bat        
├── setup_unix.sh             
└── README.md
```

---

##  Roadmap / Ideas

- [ ] Multi-hand support (two-handed drawing or gestures)
- [ ] Shape recognition (circles, lines, rectangles)
- [ ] Adjustable hover-to-click timing in a settings panel
- [ ] Export drawing as a timelapse video
- [ ] Custom color picker via HSV wheel



---

<p align="center">Built with , OpenCV, and MediaPipe.</p>
