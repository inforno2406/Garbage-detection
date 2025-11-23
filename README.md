# Garbage-detection
🗑️ Garbage Detection System (IPBS-DS) - Phase I

🌟 Project Overview

This project, IPBS-DS (Phase I), focuses on creating the intelligent core for an automated recycling system. The primary goal of this phase is to achieve real-time, high-accuracy detection and logging of plastic bottles using computer vision.

The system utilizes a custom-trained YOLOv8 object detection model on a laptop host to process live video feed. This setup successfully verifies the presence of recyclable items and logs the events to a database, while simulating the command necessary for future integration with a physical sorting mechanism.

🚀 Features (Phase I Implementation)

Real-Time Object Detection: Detects plastic bottles in a live video stream using a custom YOLOv8 model.

High Confidence Verification (FR1.2): Achieves an mAP of over 90% for the target class.

Detection Event Logging (FR2.0): Logs successful detection events (timestamp, confidence, bounding box) to an SQLite database and asynchronously synchronizes with a cloud service (e.g., Firebase).

System Status Display (FR3.0): Overlays real-time status messages and bounding boxes onto the video feed.

Actuation Simulation (FR4.0): Prints a simulated serial command to the console (e.g., "CMD: OPEN_GATE") to prepare for Phase II hardware integration.

🛠️ Technologies & Tools Used

Category

Technology/Tool

Purpose

Model

YOLOv8 (Custom Trained)

State-of-the-art object detection model for high-speed inference.

Framework

Python

Primary programming language for the host application.

ML Library

Ultralytics, PyTorch / TensorFlow

Used for model loading, inference, and video processing.

Vision

OpenCV (cv2)

Used for video stream handling and visualization.

Database

sqlite3 (Local), Firebase SDK (Cloud)

Event logging and data persistence.

Versioning

Git

Version control management for the project.

⚙️ Steps to Install & Run the Project

This project is designed to run on a host machine with a webcam and requires Python 3.8+ environment setup.

1. Prerequisites

Install Python 3.8+.

Ensure your laptop webcam is functional and accessible.

2. Clone the Repository

git clone [[https://github.com/](https://github.com/)][YourUsername]/IPBS-DS.git
cd IPBS-DS/host_application


3. Setup Python Environment

Create and activate a virtual environment (recommended):

python -m venv venv
source venv/bin/activate  # On Linux/macOS
# .\venv\Scripts\activate  # On Windows


4. Install Dependencies

Install all necessary Python packages:

pip install -r requirements.txt


(The requirements.txt should contain: ultralytics, opencv-python, sqlite3, firebase-admin, etc.)

5. Add Custom Model Weights

Place your trained YOLOv8 model file in the appropriate location:

Download your custom yolov8_bottle_detector.pt weight file.

Place it in the host_application/models/ directory.

6. Run the Application

Execute the main application file. This will open a new window showing the live webcam feed with bounding boxes.

python MainApplication.py


(Note: Ensure you have configured your Firebase credentials or API key if cloud logging is enabled.)

🧪 Instructions for Testing

Testing focuses on verifying the accuracy (FR1.2) and speed (NFR1.0) of the detection pipeline.

1. Real-Time Detection Test (Functional)

Run the application using python MainApplication.py.

Hold a variety of plastic bottles (different sizes, colors, and labels) in front of the webcam.

Expected Output: The system should draw an accurate bounding box and display the label "bottle" with a confidence score > 0.85. The console should print the simulated command (e.g., [SIM] Sending command: OPEN_GATE).

2. Negative Test (Validation)

Hold non-target objects (e.g., a paper cup, a book, a can) in front of the webcam.

Expected Output: No bounding box should appear. The application should maintain a "System Ready" or similar status.

3. Latency Test (Non-Functional - NFR1.0)

Monitor the frame processing time (FPS or latency printout) provided by the application's console output.

Expected Output: The latency per frame should consistently remain below the 500 milliseconds threshold specified in the NFRs.

4. Logging Test (Functional - FR2.0)

Perform 10 successful detection events.

Check the local log.db file (using an SQLite viewer) and the remote Firebase console.

Expected Output: 10 distinct records, each with a timestamp, confidence score, and confirmation of the event, should be present in both the local and cloud databases.
