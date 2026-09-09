# VisionTrack-YOLO: Stream Object Detection & Tracking Pipeline

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-green.svg)](https://opencv.org/)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-orange.svg)](https://github.com/ultralytics/ultralytics)
[![Dlib](https://img.shields.io/badge/Dlib-Object%20Tracking-purple.svg)](http://dlib.net/)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1MZdMIEWhplZ12XTHeijMeNgZXfGjAvZE)

An end-to-end computer vision pipeline designed for seamless video stream acquisition, robust correlation-based object tracking, and deep learning-powered multi-class object detection.

---

## 📌 Overview

This project bridges stream extraction, correlation tracking, and deep learning inference:
1. **Dynamic Stream Resolving**: Automatically resolves direct playable streams from Instagram Reels, YouTube URLs, web media, or local video files via `yt-dlp`.
2. **Real-time Object Tracking**: Uses **Dlib's Correlation Tracker** to track designated target objects frame-by-frame with high temporal consistency and low computational overhead.
3. **Deep Learning Object Detection**: Integrates **Ultralytics YOLOv8** (`yolov8n.pt`) to detect, categorize, and score multi-class objects across video frames.
4. **Visual Overlays & Rendering**: Draws annotated bounding boxes, confidence scores, and tracking paths using **OpenCV** and renders visualization sequences.

---

## 🚀 Key Features

* **Multi-Source Support**: Seamlessly processes web video links (Instagram, YouTube, direct MP4) as well as local video files.
* **Dual-Engine Processing**:
  * **Dlib**: For fast object tracking without needing continuous inference.
  * **YOLOv8**: For state-of-the-art object detection and classification.
* **Colab Ready**: Includes automated dependency installation scripts for quick deployment in Google Colab environments.
* **Interactive Visualization**: Frame-by-frame inspection and progress monitoring.

---

## 🛠 Pipeline Architecture

```
[ Video Source (URL / Local / Instagram / YouTube) ]
                         │
                         ▼
        [ Stream Resolver (yt-dlp) ]
                         │
                         ▼
        [ Frame Capture (OpenCV VideoCapture) ]
                         │
         ┌───────────────┴───────────────┐
         ▼                               ▼
 [ Dlib Object Tracker ]         [ YOLOv8 Object Detector ]
   - Correlation tracking          - Multi-class recognition
   - Bounding box persistence      - Confidence scoring
         │                               │
         └───────────────┬───────────────┘
                         ▼
        [ Frame Annotation & Visualization ]
                         │
                         ▼
               [ Processed Video Output ]
```

---

## 📦 Installation & Setup

### Option 1: Run in Google Colab (Recommended for GPU)
Simply open the notebook in Colab using the badge above and run the setup cell:
```bash
!apt-get update
!apt-get install -y cmake build-essential pkg-config python3-dev libboost-all-dev libatlas-base-dev gfortran
!pip install -r requirements.txt
```

### Option 2: Local Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AMPoet/Video-Processor.git
   cd Video-Processor
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

> **Note on Dlib (Windows):** Ensure you have Visual Studio C++ Build Tools installed along with `cmake` prior to installing `dlib`.

---

## 💻 Usage

Launch Jupyter Notebook or Jupyter Lab:
```bash
jupyter notebook Video_Processor.ipynb
```

### Configuring Video Source
In the notebook configuration cell, set your desired video source:
```python
# Web URL (Instagram, YouTube, direct link)
video_path = 'https://www.instagram.com/reel/DcYtM5TT0ko/'

# Or local video file
# video_path = 'data/sample_video.mp4'

# Resolve stream URL
stream_url = get_direct_video_url(video_path)
```

---

## 📋 Requirements

* `opencv-python>=4.8.0`
* `dlib>=19.24.0`
* `ultralytics>=8.0.0`
* `yt-dlp>=2023.7.6`
* `numpy>=1.22.0`
* `matplotlib>=3.5.0`
* `ipython>=8.0.0`

---

## 👤 Author

* **Mohammad (AMPoet)** - [GitHub Profile](https://github.com/AMPoet)

---

## 📄 License

This project is licensed under the MIT License.
