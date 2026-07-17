# Brainwave-2.0
Brainwave 2.0 - AI Powered Interview & Social Skills Development Platform

Prototype Video Link: https://youtu.be/skzAe78GBiU?si=Gcg4boW4Fn9-9Jno

An AI-powered full-stack platform that helps users improve interview performance by combining adaptive AI interviewing with real-time confidence analysis using Machine Learning, Computer Vision, and Voice Analytics.

Overview

Brainwave 2.0 is a MERN stack application designed to help users prepare for interviews while simultaneously improving their communication and confidence.

Unlike traditional interview preparation platforms, Brainwave evaluates both what you say and how you say it.

The system combines:

🤖 Adaptive Interview AI
🎤 Voice Confidence Detection
📷 Face & Body Language Analysis
📊 Performance Analytics
🧠 Custom Machine Learning Models
✨ Gemini AI Integration

The goal is to simulate realistic interview experiences while providing objective feedback that helps users reduce anxiety and continuously improve.

Features
AI Interview Intelligence

Users simply upload:

Resume
Desired Job Role

The system generates interview questions tailored specifically to the user's profile using Google's Gemini AI.

Adaptive Question Difficulty

Instead of asking random questions, Brainwave dynamically adjusts interview difficulty.

Difficulty ranges from 1 – 10
Interview always starts at Level 5

If the candidate answers correctly:

Next question becomes harder.

If the candidate answers incorrectly:

Next question becomes easier.

This creates a personalized interview experience similar to real technical interviews.

Intelligent Scoring System

Each correctly answered question awards points equal to its difficulty level.

Example:

Question	Difficulty	Correct?	Total Score
Q1	5	✅	5
Q2	6	✅	11
Q3	7	❌	11
Q4	6	✅	17

Answer Score:

Answer Score = Total Difficulty Points / Number of Questions

Final Interview Score:

Final Score =
0.7 × Answer Score
+
0.3 × Confidence Score

The final score estimates the candidate's interview readiness by combining knowledge and confidence.

Confidence Analysis

Brainwave doesn't only evaluate answers—it also evaluates user confidence in real time.

Confidence analysis is performed using two independent AI pipelines:

Voice Confidence Detection
Face & Body Language Detection
Voice Confidence Detection

The system continuously analyzes the user's voice during the interview.

Unlike traditional frame-by-frame processing, Brainwave processes audio in 1.4-second windows, producing significantly more stable predictions.

Processing Pipeline
1. Audio Collection

Microphone frames are continuously collected.

Approximately 30 frames are grouped into one audio segment.

2. Silence Detection

Before processing, the system checks whether the user is actually speaking.

Background noises such as:

Fan
AC
Keyboard
Room noise

are ignored automatically.

3. Feature Extraction

The audio signal is converted into numerical features including:

Pitch
Jitter
Speaking Speed
Voice Stability
4. ML Prediction

The extracted features are passed into a custom-trained Random Forest classifier, which predicts confidence levels such as:

Confident
Nervous

Example output:

Confidence : 85%
Prediction : Confident
Face & Body Confidence Detection

Brainwave also evaluates non-verbal communication.

Using MediaPipe Pose, the application tracks 33 body landmarks in real time while ensuring complete privacy.

No video recordings are stored.

Important landmarks include
Nose
Ears
Wrists
Shoulders

The system processes approximately 30 frames per second.

Behavioral Metrics

The platform computes several physics-based movement metrics including:

Hand Tremor (Jerk)
Body Sway (Variance)
Head Yaw
Eye Contact Stability
Motion Consistency

These features are passed into a custom-trained XGBoost model, trained using 100+ real interview recordings.

Live Feedback

The confidence model predicts behavioral traits in real time and provides actionable suggestions such as:

Maintain better eye contact
Reduce unnecessary hand movements
Keep a stable posture
Speak with a consistent pace

###Technology Stack

Frontend
React.js
Tailwind CSS
JavaScript
Axios
Backend
Node.js
Express.js
MongoDB
JWT Authentication
Artificial Intelligence
Google Gemini API
Prompt Engineering
Machine Learning
Random Forest
XGBoost
Scikit-learn
Computer Vision
MediaPipe Pose
OpenCV
Audio Processing
Librosa
NumPy
Python
