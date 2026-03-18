# PowerPoint Gesture Control Assistant
![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-active-success)

A sophisticated computer vision-based system that enables hands-free control of PowerPoint presentations using hand gestures, facial recognition authentication, and real-time emotion detection.

## Features

### Core Functionality
- **Hand Gesture Recognition**: Control PowerPoint presentations using intuitive hand gestures
- **Facial Recognition Authentication**: Secure user authentication using DeepFace
- **Real-time Emotion Detection**: Monitors presenter's emotions and can auto-pause presentations
- **Custom Gesture Training**: Create and train your own custom gestures
- **Camera Calibration**: Built-in camera calibration for improved accuracy
- **PowerPoint Integration**: Direct PowerPoint COM API integration with keyboard fallback

### Built-in Gestures

Gesture | Action
---|---
Open palm (all fingers extended) | Start Presentation
Index finger pointing | Next Slide
Pinky finger extended | Previous Slide
Closed fist | End Presentation

### Advanced Features
- Voice feedback for gesture actions
- Multi-user support with face registration
- Auto-pause on negative emotions (confusion, anger, etc.)
- Customizable cooldown periods for gesture detection
- Visual feedback with real-time overlay
- Logging system for debugging and monitoring

## Requirements
- Python 3.8 or higher
- Webcam
- Windows OS (for PowerPoint COM API integration)
- PowerPoint installed (optional, falls back to keyboard simulation)

---

## Installation

### 1) Clone the Repository

> ✅ Use the actual repository URL (not the placeholder).

```bash
git clone https://github.com/mohamed-eldagla/gesture-controlled-presentation.git
cd gesture-controlled-presentation
```

### 2) Create a Virtual Environment (Recommended)

#### Windows (PowerShell)
```powershell
python -m venv venv
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
```

#### Windows (CMD)
```bat
python -m venv venv
venv\Scripts\activate.bat
python -m pip install --upgrade pip
```

#### macOS / Linux
```bash
python -m venv venv
source venv/bin/activate
python -m pip install --upgrade pip
```

### 3) Install Dependencies (Required: use constraints)

To avoid dependency conflicts between **MediaPipe / TensorFlow / protobuf**, install using the constraints file:

```bash
pip install -r requirements.txt -c constraints.txt
```

> **Do not** run `pip install -r requirements.txt` without constraints.
> The project dependency set can become unstable depending on the latest upstream releases.

### 4) Quick Sanity Checks (Optional but Recommended)

```bash
python -c "import mediapipe as mp; print('mediapipe:', mp.__version__)"
python -c "import google.protobuf as pb; print('protobuf:', pb.__version__)"
python -c "import tensorflow as tf; print('tensorflow:', tf.__version__)"
python -c "import cv2; print('opencv:', cv2.__version__)"
```

### 5) Run the Application

```bash
python main.py
```

`main.py` is the monolithic “ready to run” version.

---

## Usage

### Getting Started
1. **Register Your Face**
   - Navigate to the "User Management" tab
   - Click "Register New User"
   - Enter your username and capture your face
2. **Authenticate**
   - Click the "Authenticate" button in the main control panel
   - The system will recognize and authenticate you
3. **Start Detection**
   - Click "Start Detection" to begin gesture recognition
   - Open your PowerPoint presentation
   - Use hand gestures to control the presentation

### Creating Custom Gestures
1. Navigate to the "Gesture Training" tab
2. Enter a name for your custom gesture
3. Select the action you want to associate with it
4. Click "Start Training"
5. Position your hand in the desired gesture
6. Click "Capture Gesture" to save

### Camera Calibration
For improved accuracy, calibrate your camera:
1. Print a chessboard calibration pattern
2. Click "Calibrate Camera" in the main tab
3. Follow the on-screen instructions
4. Move the chessboard pattern to different positions

---

## Configuration

### Settings
Adjust application settings in the "Settings" tab:
- **Gesture Cooldown**: Time between gesture detections (default: 1.5s)
- **Voice Feedback**: Enable/disable voice announcements
- **Emotion Detection**: Toggle emotion monitoring
- **Auto-pause on Confusion**: Automatically pause when negative emotions detected

---

## Project Structure
This repository contains both **monolithic** and **modular** code structures:

### Quick Start (Monolithic)
```
main.py  # All-in-one file (1,260 lines) - Ready to run!
```

### Professional Structure (Modular)
```
src/
├── vision/  # Computer vision modules
│   ├── gesture_detector.py  # Hand gesture detection
│   ├── face_recognizer.py   # Face recognition
│   ├── emotion_detector.py  # Emotion detection
│   └── camera_calibrator.py # Camera calibration
├── control/  # Presentation control
│   └── presentation_controller.py
├── data/  # Data persistence
│   └── database.py  # User/gesture/calibration DBs
└── utils/  # Utilities
    └── logger.py  # Logging configuration
```

**See [MODULAR_VS_MONOLITHIC.md](MODULAR_VS_MONOLITHIC.md) for detailed comparison**

### Generated Files (Not in Git)
```
gesture_control.log       # Application logs
users_db.pkl              # User face database
custom_gestures.json      # Custom gestures
camera_calibration.json   # Camera calibration data
```

---

## Technologies Used
- **OpenCV**: Real-time computer vision
- **MediaPipe**: Hand and face landmark detection
- **DeepFace**: Facial recognition and emotion detection
- **Tkinter**: GUI framework
- **PyAutoGUI**: Keyboard simulation fallback
- **pyttsx3**: Text-to-speech for voice feedback
- **comtypes**: PowerPoint COM API integration (Windows)

---

## Troubleshooting

### Common Issues

**Camera not detected**
- Ensure your webcam is properly connected
- Check if other applications are using the camera
- Verify camera permissions

**Face recognition not working**
- Ensure good lighting conditions
- Position your face clearly in front of the camera
- Register multiple images for better accuracy

**PowerPoint integration fails**
- Ensure PowerPoint is installed (Windows only)
- The system will automatically fall back to keyboard simulation
- Check that PowerPoint is not in restricted mode

**Gestures not detected**
- Ensure adequate lighting
- Position your hand clearly in the camera frame
- Adjust cooldown period in settings if gestures fire too rapidly

---

## Performance Tips
- Use a high-quality webcam for better detection
- Ensure consistent lighting conditions
- Close unnecessary applications to improve processing speed
- Perform camera calibration for optimal accuracy

---

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.
See [CONTRIBUTING.md](CONTRIBUTING.md) for more details.

---

## Future Enhancements
- [ ] Support for macOS and Linux
- [ ] Multiple hand gesture support
- [ ] Integration with other presentation software (Keynote, Google Slides)
- [ ] Web-based interface
- [ ] Mobile app companion
- [ ] Advanced gesture customization
- [ ] Multi-language support
- [ ] Cloud-based user profiles

---

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- MediaPipe by Google for hand tracking
- DeepFace for facial recognition capabilities
- OpenCV community for computer vision tools

## Contact
For questions or support, please open an issue on GitHub.

## Citation
If you use this project in your research or work, please cite:
```bibtex
@software{powerpoint_gesture_control,
  author = {Mohamed Eldagla},
  title = {PowerPoint Gesture Control Assistant},
  year = {2024},
  url = {https://github.com/mohamed-eldagla/powerpoint-gesture-control}
}
```

---

**Note**: This application requires a webcam and is optimized for Windows systems with PowerPoint installed. The application gracefully falls back to keyboard simulation on systems without PowerPoint.
