AI-Powered Surveillance & Face Recognition System
A robust, multi-threaded security application that combines real-time motion detection with deep-learning face recognition. This system is designed for home or small office security, providing automated logging and visual alerts.

🚀 Key Features
Multi-Threaded Architecture: Separate threads for frame grabbing, face analysis, and database logging to ensure zero-lag performance.

Intelligent Motion Trigger: Analysis only runs when motion is detected, significantly reducing CPU/GPU overhead.

SQL Database Logging: Thread-safe SQLite integration for permanent record-keeping of every recognized individual.

Automatic Stranger Capture: Instantly saves snapshots of unrecognized faces to a dedicated security folder.

Professional Enrollment GUI: A secondary custom Tkinter application for high-quality biometric data collection.

Signature Caching: Uses Python Pickling to store face encodings, allowing the system to boot in seconds regardless of the dataset size.

🏗️ System Architecture
The project is split into two main components: the Recognition Engine and the Enrollment Portal.

1. Recognition Engine (main.py)
This is the "brain" of the system. It handles the live stream and decision-making logic.

Why OpenCV? Used for high-speed image processing, frame manipulation, and motion thresholding.

Why Face_Recognition (dlib)? Utilizes a state-of-the-art dlib model with 99.38% accuracy on the Labeled Faces in the Wild benchmark.

Why Threading? * Thread A (Grabber): Prevents "frame lag" by keeping the buffer empty.

Thread B (Analyzer): Performs heavy math without freezing the video display.

Thread C (Logger): Ensures database writes don't stall the AI logic.

2. Enrollment Portal (enrollment.py)
A modern UI built with CustomTkinter to onboard new users.

Visual Feedback: Uses Haar Cascades to guide the user to center their face.

Automatic Cache Invalidation: When a new person is added, the app automatically clears the old face signatures to force a rebuild on the next system start.
