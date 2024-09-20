# Crowd Detection and Alert System

This project uses Yolov5 to detect people in a video stream and raises an alert when more than **n** people are detected continuously for over **m** seconds. It captures a screenshot when the condition is met, and saves the image.

## Features

- **YOLOv5 for Crowd Detection**: Utilizes the powerful YOLOv5 model for real-time object detection.
- **Custom Object Detection**: **Head detection** instead of person (full-body) detection is used to improve accuracy in scenarios where:
  - The camera may not capture the entire body.
  - Crowded environments might obscure individuals, making full-body detection unreliable.
  
  Using head detection allows the system to still track people even when their full bodies are not visible, overcoming these challenges effectively.
- Tracks the number of people visible in the video.
- **SORT Algorithm for Tracking**: The **SORT (Simple Online and Realtime Tracking)** algorithm is implemented for robust tracking of detected heads. This helps in maintaining consistency of detection across frames, especially in crowded environments.
- Captures a screenshot when more than **n** people are detected for **m** continuous seconds.


## Requirements

- Python 3.x
- OpenCV
- Numpy
- PyTorch
- YOLOv5

All the necessary libraries can be referred to using the `requirements.txt` file provided in the repository.



## Run

```bash
$ python3 detect_main.py --weights weights/crowd_yolov5m.pt --source video1.mp4 --view-img --n_people 2 --n_seconds 1
```
  
  
## Output

  
