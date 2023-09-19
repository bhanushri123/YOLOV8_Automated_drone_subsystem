import cv2
import math
import serial
from ultralytics import YOLO

# Initialize YOLO model
model = YOLO('200epo.pt')

# Initialize video capture from the default camera (change the index if using a different camera)
cap = cv2.VideoCapture(0)

# Define the threshold distance
threshold_distance = 50.0  # Adjust this value as needed

while True:
    # Read frame from camera
    ret, frame = cap.read()

    # Perform object detection
    results = model.predict(frame)

    detected = False  # Initialize detection flag
    centroid = None  # Initialize centroid

    for result in results:
        if len(result.pred) > 0:  # Check if any boxes are detected
            for pred in result.pred[0]:
                x1, y1, x2, y2, conf, cls = pred.tolist()
                bbox_centroid = ((x1 + x2) / 2, (y1 + y2) / 2)
                # Draw bounding box on the frame
                cv2.rectangle(frame, (int(x1), int(y1)), (int(x2), int(y2)), (0, 255, 0), 2)
                # Draw centroid on the frame
                cv2.circle(frame, (int(bbox_centroid[0]), int(bbox_centroid[1])), 5, (0, 255, 0), -1)

                # Calculate distance between camera centroid and bounding box centroid
                camera_centroid = (frame.shape[1] / 2, frame.shape[0] / 2)
                distance = math.sqrt((bbox_centroid[0] - camera_centroid[0]) ** 2 + (bbox_centroid[1] - camera_centroid[1]) ** 2)

                if distance < threshold_distance:
                    detected = True
                    centroid = bbox_centroid
                    break  # Exit the loop if distance is less than threshold

    # Display frame with bounding boxes and centroid
    cv2.imshow("Fire Detection", frame)

    # Check for 'q' key press to exit the loop
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

    # Check if fire is detected
    if detected:
        print("Fire Detected")
        print("Centroid:", centroid)
        print("True")
        myCmd = '1'
        myCmd = myCmd + '\n'
        arduinoData.write(myCmd.encode())
        # Stop the code execution if fire is detected

# Release video capture and close windows
cap.release()
cv2.destroyAllWindows()

# Output the result
if not detected:
    print("No fire detected")
    print("False")
    myCmd = '0'
    myCmd = myCmd + '\n'
    arduinoData.write(myCmd.encode())
