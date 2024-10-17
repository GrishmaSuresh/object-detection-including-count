# YOLOv8 Live Object Detection

This Python project demonstrates live object detection using a webcam feed and YOLOv8, with detection annotations and zone-based triggering.

## Features

- **Live Object Detection**: Uses the YOLOv8 model to perform real-time object detection from a webcam feed.
- **Detection Annotations**: Bounding boxes and labels are drawn around detected objects.
- **Polygon Zone Triggering**: A custom polygonal zone is defined, and detection events within the zone are highlighted.

## Requirements

- Python 3.x
- OpenCV
- Ultralytics YOLOv8
- Supervision (for handling annotations and polygon zones)
- NumPy

## Installation

1. Clone the repository:
 ```bash
 git clone https://github.com/yourusername/yolov8-live-detection.git
 ```
2. Install the required dependencies:
```bash
  pip install opencv-python ultralytics supervision numpy
```
3. Download the YOLOv8 model weights (yolov8l.pt):
- Visit the Ultralytics YOLOv8 GitHub or use the command:
```bash
yolo download model=yolov8l.pt
```

## Usage
1. Run the script with the following command:

```bash
python yolov8_live.py --webcam-resolution 1280 720
```
You can adjust the webcam resolution by providing different width and height values.

2. The webcam feed will open, and live object detection will be displayed with bounding boxes and labels.

3. The defined zone will highlight objects detected within the zone.

4. Press the Esc key to close the webcam feed.

## How It Works
- **YOLOv8 Model:** The script uses YOLOv8 for object detection, excluding class 0 (person) detections.

- **Bounding Box Annotation:** Detected objects are annotated with bounding boxes and class labels.

- **Polygon Zone:** A custom polygon zone is defined, and detections inside this zone are tracked and highlighted.

  The zone polygon coordinates are defined as:

```python
ZONE_POLYGON = np.array([
    [0, 0],
    [0.5, 0],
    [0.5, 1],
    [0, 1]
])
```
This can be adjusted to customize the area where detections trigger an event.

## Example Output
Once the webcam feed starts, the frame will display:

- Detected objects with bounding boxes and labels (e.g., car 0.85).
- Objects inside the predefined polygon zone will trigger zone-specific annotations.
  
## Arguments
--webcam-resolution [WIDTH HEIGHT]: Set the webcam resolution (default: 1280x720).
Troubleshooting
Webcam Not Detected: Ensure your webcam is connected and the correct device index is being used in cv2.VideoCapture().
No Objects Detected: Ensure the YOLOv8 model is correctly loaded and that the webcam feed has sufficient lighting for detection.
Future Enhancements
Add support for more object classes or specific class filtering.
Extend zone functionality to dynamically change shape or size.
Improve performance with hardware acceleration or multi-threading.
License
MIT License
