# YOLOV8_Automated_drone_subsystem
Certainly! Here's an explanation of the purpose of the provided code for your GitHub readme file:

**Title: Real-time Fire Detection with YOLO and Arduino Integration**

**Overview:**
This project aims to create a real-time fire detection system using the YOLO (You Only Look Once) object detection model. The primary objective is to detect fires within a live video stream from a camera and trigger an action (in this case, communication with an Arduino board) upon fire detection.

**Key Components:**

1. **YOLO Model:** The code initializes a YOLO object detection model using a pre-trained model file named '200epo.pt.' YOLO is used to identify objects in each frame of the video feed.

2. **Video Capture:** The code captures video frames in real-time from the default camera (you can change the camera index if needed). These frames are then processed by the YOLO model.

3. **Fire Detection:** YOLO analyzes each frame to detect fire. When a fire is detected, the code highlights the fire's location with bounding boxes and calculates the centroid of the detected fire.

4. **Threshold Distance:** A threshold distance is defined to determine the proximity of the detected fire to the camera's center. If the fire is within this threshold distance, it is considered a valid detection.

5. **Arduino Integration:** In case of fire detection, the code communicates with an Arduino board by sending a command ('1'). This integration can trigger actions such as sounding an alarm, activating fire suppression systems, or sending alerts.

**Purpose:**
The purpose of this code is to create a real-time fire detection system that can be integrated with other hardware components, such as Arduino, to take immediate actions in response to fire incidents. This system can be used in various applications, including fire safety and security, to provide timely alerts and responses to potential fire hazards.

**Usage:**
1. Ensure you have the YOLO model file ('200epo.pt') in the working directory.
2. Run the code, and it will capture video from the default camera.
3. When a fire is detected within the specified threshold distance, the code communicates with the Arduino board to trigger an action.
4. Press 'q' to exit the application.

**Note:**
- Make sure to adjust the threshold_distance as needed to suit your specific environment.
- Additional actions and notifications can be integrated with the Arduino code as per your requirements.

This project provides a foundation for building real-time fire detection systems with hardware integration, enhancing safety measures in various settings.
