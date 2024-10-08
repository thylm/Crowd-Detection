# Crowd Detection and Alert System

This project uses Yolov5 to detect people in a video stream and raises an alert when more than **n** people are detected continuously for over **m** seconds. It show an alert message on the screen and captures a screenshot when the condition is met and saves the alert images.

## Features

- **YOLOv5 for Crowd Detection**: Utilizes the powerful YOLOv5 model for real-time object detection.
- **Custom Object Detection**: **Head detection** instead of person (full-body) detection is used to improve accuracy in scenarios where:
  - The camera may not capture the entire body.
  - Crowded environments might obscure individuals, making full-body detection unreliable.
  
  Using head detection allows the system to still track people even when their full bodies are not visible, overcoming these challenges effectively.
- Tracks the number of people visible in the video.
- **SORT Algorithm for Tracking**: The **SORT (Simple Online and Realtime Tracking)** algorithm is implemented for robust tracking of detected heads. This helps in maintaining consistency of detection across frames, especially in crowded environments.
- Captures a screenshot when more than **n** people are detected for **m** continuous seconds.

## The approach and steps
1. Head Detection:
- The system utilizes the YOLOv5 model to detect heads in each frame of the video stream.
2. Tracking (SORT Algorithm):
- Tracking is essential to ensure that the same head is consistently identified, even if it moves slightly or overlaps with other heads.
- This ensures that the same head is not detected multiple times in subsequent frames, providing more accurate tracking over time.
3. Thresholds for Alert:
- The system counts the number of detected heads in a defined region of interest (ROI) per frame.
- If the number of heads exceeds a certain threshold (e.g., more than 4 people) continuously for a set time (e.g., 2 minutes), the system triggers an alert.
- An alert can be an action like saving a frame, pop-up a notification on screen.

## Requirements

- Python 3.x
- OpenCV
- Numpy
- PyTorch
- YOLOv5

All the necessary libraries can be referred to using the `requirements.txt` file provided in the repository.



## Run

```bash
$ python3 detect_main.py --weights crowd_yolov5m.pt --source video1.mp4 --view-img --n_people 2 --n_seconds 1
```

## 👋 
Download the trained **weight** and view the **output video** of the detection process [here](https://drive.google.com/drive/folders/124KqE8etgj5Ioo_PRLzSpF4BMdhHyRf5?usp=sharing)

## Input videos
- https://www.pexels.com/video/people-are-walking-up-an-escalator-with-a-person-19319544/
- https://www.pexels.com/video/night-food-market-4512876/

## Output

**Crowd Detection Alert Images**
![crowd](https://github.com/thylm/crowd-detection/blob/main/results/alert_127.jpg)

![crowd](https://github.com/thylm/crowd-detection/blob/main/results/alert_90.jpg)

**Head Detection**
![head](https://github.com/thylm/crowd-detection/blob/main/results/test.jpg)
  
