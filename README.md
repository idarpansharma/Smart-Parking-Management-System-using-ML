# 🚗 Smart Parking Management System using ML

A real-time parking space detection system that uses computer vision and machine learning techniques to identify available parking spaces in a parking lot. The system processes video feeds and provides instant visual feedback on parking availability.

## 📸 Project Showcase

![Parking Space Detection](/output.png)

## 🎯 Features

- **Real-time Parking Detection**: Continuously monitors video feed to detect occupied and available parking spaces
- **Visual Indicators**: 
  - 🟢 **Green rectangles** = Available parking spaces
  - 🔴 **Red rectangles** = Occupied parking spaces
- **Live Availability Counter**: Displays total free parking spaces vs. total spaces
- **Space Counting**: Shows pixel count for each space to determine occupancy status
- **Interactive Space Picker**: GUI tool to manually mark parking spaces on an image
- **Persistent Storage**: Saves parking space coordinates for repeated use

## 🛠️ Technologies Used

- **Python 3.9+**
- **OpenCV (cv2)** - Computer vision processing
- **NumPy** - Numerical computations
- **CVZone** - Enhanced OpenCV utilities for text rendering

## 📋 Requirements

```
opencv-python
cvzone
numpy
```

## 🚀 Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd Smart-Parking-Management-System-using-ML
```

2. Create and activate a virtual environment:
```bash
python3 -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. Install required packages:
```bash
pip install opencv-python cvzone numpy
```

## 📖 Usage

### Method 1: Run the Main Detection System

Run the parking space detection on video:
```bash
python main.py
```

The system will:
- Load the video file (`carPark.mp4`)
- Load previously marked parking spaces from `CarParkPos`
- Process each frame in real-time
- Display parking availability with visual indicators
- Show individual space pixel counts

### Method 2: Set Up Parking Spaces (First Time)

If this is your first time or you want to mark new parking spaces:

```bash
python ParkingSpacePicker.py
```

**Controls:**
- **Left Click**: Add a parking space at that location
- **Right Click**: Remove a parking space at that location
- Saved coordinates are automatically stored in `CarParkPos` file

## 🔍 How It Works

### Image Processing Pipeline:

1. **Grayscale Conversion**: Convert colored video frames to grayscale
2. **Gaussian Blur**: Apply blur to reduce noise
3. **Adaptive Thresholding**: Convert to binary image with ADAPTIVE_THRESH_GAUSSIAN_C
4. **Median Blur**: Further noise reduction
5. **Dilation**: Enhance foreground objects using morphological operations
6. **Space Detection**: Analyze each marked parking space region
7. **Occupancy Classification**: Compare pixel counts with threshold (900 pixels)

### Detection Logic:

- **Pixel Count < 900**: Space is available (empty) - marked GREEN
- **Pixel Count ≥ 900**: Space is occupied - marked RED

## 📁 Project Structure

```
Smart-Parking-Management-System-using-ML/
├── ps/
│   ├── main.py                 # Main parking detection system
│   ├── ParkingSpacePicker.py   # Utility to mark parking spaces
│   ├── carPark.mp4             # Input video file
│   ├── carParkImg.png          # Reference parking lot image
│   └── CarParkPos              # Stored parking space coordinates (binary)
└── README.md                    # This file
```

## ⚙️ Configuration

You can customize the following parameters in `main.py`:

```python
width, height = 107, 48           # Parking space dimensions (in pixels)
threshold_value = 900             # Pixel count threshold for occupancy
kernel = np.ones((3, 3), np.uint8) # Morphological operation kernel
```

## 🎮 Controls

While the detection system is running:
- **Q or ESC key**: Exit the application
- **Space bar**: Pause/Resume video playback

## 📊 Performance Metrics

- Real-time processing with minimal latency
- Adaptive thresholding for varying lighting conditions
- Robust to video noise through median and Gaussian filtering

## 🔧 Troubleshooting

| Issue | Solution |
|-------|----------|
| "File not found" error for `carPark.mp4` | Ensure video file is in the `ps/` directory |
| "CarParkPos not found" error | Run `ParkingSpacePicker.py` first to generate parking space coordinates |
| Low detection accuracy | Re-calibrate parking spaces using `ParkingSpacePicker.py` or adjust the pixel threshold value |
| Poor performance on Mac | Ensure OpenCV is properly installed with native optimizations |

## 🎓 Learning Concepts

This project demonstrates:
- Real-time computer vision processing
- Image segmentation and morphological operations
- Object detection using pixel analysis
- Python GUI development with OpenCV
- File I/O with binary pickle format

## 📝 Future Enhancements

- [ ] Deep learning model for improved accuracy
- [ ] Multi-camera support
- [ ] Database integration for historical data
- [ ] Web dashboard for remote monitoring
- [ ] Mobile app for user notifications
- [ ] IoT integration with parking sensors

## 📄 License

This project is open source and available for educational purposes.

## 👨‍💻 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## 📧 Contact

For questions or suggestions, please reach out to the project maintainers.

---

**Last Updated**: April 2026  
**Python Version**: 3.9+  
**Status**: Active & Maintained
