🚗 Automatic Vehicle & License Plate Detection System

This project implements a real-time vehicle detection, tracking, and license plate recognition system using YOLOv8, EasyOCR, and Kalman filter-based SORT tracking.
The pipeline takes a video as input, detects vehicles and license plates, recognizes plate numbers, and outputs a processed video with annotated bounding boxes and license plate information.

📌 Features

Detects vehicles (cars, trucks, buses, motorcycles) using YOLOv8.

Detects license plates using a custom-trained YOLO model.

Tracks vehicles across frames with SORT (Kalman Filter + Hungarian Algorithm).

Reads license plates with EasyOCR and corrects misclassified characters.

Interpolates missing bounding box data for smoother results.

Generates an output video with annotated vehicles and license plates.

📂 Project Structure
LPR/
│── new.py                     # Main pipeline script
│── bus.py                     # Bus detection module
│── sample.mp4                 # Example input video
│── yolov8n.pt                  # Pretrained YOLOv8 model
│── license_plate_detector.pt   # Custom license plate detector model
│── out.mp4                     # Output video (generated)
│── .gitignore

⚙️ Installation
1️⃣ Create Virtual Environment
# Create venv (Python 3.10 recommended)
python -m venv venv

# Activate venv
# On Windows:
venv\Scripts\activate
# On Linux/Mac:
source venv/bin/activate

2️⃣ Install Dependencies
pip install -r requirements.txt


If you don’t have a requirements.txt, install manually:

pip install ultralytics opencv-python-headless numpy pandas scipy easyocr filterpy lap


⚠️ If lap gives errors, you can skip it (code falls back to scipy.optimize).

▶️ Usage

Run the pipeline with:

python new.py


It will:

Load sample.mp4

Detect and track vehicles + license plates

Recognize plate numbers

Save annotated output to out.mp4

🧪 Example Output

Green bounding boxes → detected vehicles

Red boxes → license plates

Extracted license plate crops + text displayed above vehicles

📝 Notes

Update video_path in new.py if you want to process another video.

Make sure yolov8n.pt and license_plate_detector.pt are in the same directory.

Output video is saved as out.mp4 by default.

🚀 Future Improvements

Add real-time RTSP stream support

Improve OCR accuracy with region-specific license plate formats

Export detections to CSV/Database for analytics