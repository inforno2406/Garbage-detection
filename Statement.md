Project Statement: Garbage Detection System (IPBS-DS) - Phase I

1. Problem Statement

The contamination of recycling streams by non-recyclable items is a significant challenge for waste management facilities, leading to increased processing costs and the rejection of otherwise valuable recyclable material. A large volume of clean PET plastic bottles is currently lost to landfills due to improper and mixed disposal habits at the consumer level.

The problem is to develop a reliable, immediate, and automated solution that can accurately identify and verify the presence of PET plastic bottles at the point of disposal, thereby ensuring a cleaner, more segregated, and ultimately more valuable recycling input stream.

2. Scope of the Project (Phase I: Detection & Logging)

This project is implemented in Phase I and focuses exclusively on the Intelligent Detection and Data Logging components.

Aspect

Detail

Current Scope (Implemented)

Real-time object detection using a custom-trained YOLOv8 model on a laptop webcam feed, event logging (timestamp, confidence) to a persistent database, and simulation of the actuation command.

Excluded from Current Scope (Future Enhancement)

The physical sorting mechanism (motors, microcontroller, gating system), and real-time serial communication with hardware. This is reserved for Phase II.

Primary Output

A runnable Python application that performs live inference, visualizes bounding boxes, and records detection statistics.

The project scope is limited to the software pipeline necessary to perform computer vision-based garbage detection and data logging, fulfilling all Functional Requirements (FR1.0, FR2.0, FR3.0) related to vision and data.

3. Target Users

Target User Group

Interaction/Benefit

The General Public / Recycler

Primary Interaction: Interacts with the system by placing items in front of the camera. The system provides immediate visual feedback on successful item identification.

System Operator / Maintainer

Primary Interaction: Monitors the system's performance, latency, and accuracy through the live feed and the log data. Uses the logged data for quality assurance and model retraining.

Recycling Facility Management

Primary Benefit: Receives aggregated data (via cloud sync) on the volume and type of items detected, allowing for better forecasting of clean plastic bottle intake.

4. High-Level Features

The current implementation focuses on the following three major functional modules:

Feature

Description

Related FRs

A. Real-Time Vision Pipeline

Utilizes the YOLOv8 object detection model on a laptop webcam feed to process frames instantly and accurately identify plastic bottles, displaying live bounding boxes and confidence scores.

FR1.0, FR3.0

B. Detection Event Logger

Automatically logs successful detection events (confidence > 0.85) to both a local SQLite database and an asynchronous cloud service (e.g., Firebase), maintaining a persistent record of the system's activity.

FR2.0

C. Actuation Command Simulation

Implements the logical command structure for the physical sorting gate. Upon successful detection, the system simulates the necessary control signal (e.g., "CMD: OPEN_GATE") in the console, ensuring the control logic is validated for future hardware integration.
