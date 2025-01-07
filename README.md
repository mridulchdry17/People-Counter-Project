# People Counter Using YOLO and SORT Tracker

This project uses **YOLOv8** object detection and the **SORT tracker** to count people in a video feed. It implements tracking and counting functionality for objects (people) crossing defined boundaries.

## Features
- **Object Detection:** Uses YOLOv8 for detecting objects.
- **Object Tracking:** SORT (Simple Online and Realtime Tracking) for tracking individuals across frames.
- **Counting Logic:** Counts people crossing the defined "Up" and "Down" boundaries in the video.
- **Customizable Mask:** Ability to filter specific regions of interest using a mask.

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/People-Counter-Project.git
cd People-Counter-Project
```
### 2. Set Up a Virtual Environment
```bash
python -m venv env
source env/bin/activate      # On Linux/macOS
env\Scripts\activate         # On Windows
```
### 3. Install Dependencies
``` bash
pip install -r requirements.txt
```
## Usage
### 1. Place Your Files
* Video Input: Replace people.mp4 with your input video file in the project directory.
* YOLO Weights: Download YOLOv8 weights from Ultralytics YOLO and place them in the yolo-weights folder. Update the path in the code if necessary.
* Mask Image: Use mask.png to specify the region of interest (optional).
### 2. Run the Script
Run the following command to execute the script:
``` bash
python people_counter.py
```
### 3. Controls
Press q to quit the application.

## Project Workflow
#### Object Detection:
* YOLOv8 detects objects in the video stream.
* Classes are filtered to focus on "person."
#### Mask Application:
* A mask is applied to define the region of interest.
#### Object Tracking:
* SORT tracks detected objects across frames and assigns unique IDs.
#### Counting Logic:
* Counts people crossing the Up and Down boundary lines.
### File Descriptions
* people_counter.py: Main Python script for detecting, tracking, and counting.
* people.mp4: Example input video file.
* mask.png: Mask to focus on specific areas in the video.
* graphics.png: Custom overlay graphics.
#### Results
The program outputs:
* The count of people moving UP and DOWN displayed on the video.
* Tracked bounding boxes and unique IDs for individuals.
## Customization
#### Boundary Lines: Modify limitsUp and limitsDown to define new boundary coordinates:

``` python

limitsUp = [x1, y1, x2, y2]
limitsDown = [x3, y3, x4, y4] 
```
#### Class Filtering: Adjust the class filter for other objects (e.g., cars, bikes) in:
``` python
if currentClass == "person" and conf > 0.3:
```

#### Tracker Parameters: Modify SORT parameters:
``` python 
tracker = Sort(max_age=20, min_hits=3, iou_threshold=0.3)
```
## Acknowledgements
* YOLOv8: For object detection.
* SORT Tracker: For tracking logic.
* OpenCV & CVZone: For video processing and visualization.
