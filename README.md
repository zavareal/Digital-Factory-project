# Distraction Detection in Manufacturing using Project Aria Glasses

This project was developed for the *Digital Factory* course. It implements a distraction-detection system using Meta’s Project Aria glasses. The system combines eye-gaze tracking and YOLO-based object detection to determine whether an operator is focused on the correct elements during a disassembly task.

The proof of concept processes Aria VRS recordings, detects the objects involved in operation 12 of the brake disassembly, projects the operator’s gaze into the video frames, and generates a final video showing when the operator is focused or distracted.

---

## 📦 Requisites

install ultralytics library  
`!pip install ultralytics`

install aria studio libraries  
`!pip install projectaria-tools'[all]'`  
or  
`!pip install projectaria-tools`

---

## 📁 Files

### /files directory  
Contains the input data:

- **best_def.pt**: the object detection model  
- **Eye_Gaze_def.csv**: the csv file of the eye gaze observation given by MPS  
- **VRS_def.vrs**: the corresponding VRS file  

### Main project files (root)

- **functions.py**: a python file containing functions that the notebook will call. The functions are described inside the file and in the report  
- **test_video.ipynb**: the notebook that will process the VRS  
- **video_flag.mp4**: the video output of the notebook  

---

## ▶️ Steps

1. run the **test_video.ipynb** code  
2. the video will be saved by default as **video_flag.mp4** (the output name can be changed with the `output_video_path` attribute when calling the `inference_video` function)

---

## 🧩 Project Overview

### Eye Gaze Projection
- Reads 3D gaze vectors from MPS  
- Reprojects them into 2D coordinates on the RGB video frames  
- Synchronizes gaze timestamps with VRS frames  

### Object Detection (YOLOv11)
- Custom YOLOv11 model trained on brake components, screws, and the Torx tool  
- Detects objects frame-by-frame  
- Provides bounding boxes used for attention evaluation  

### Distraction Detection
- Checks whether the operator is looking at the correct objects for the task  
- Frame-level output:
  - **Green = focused**
  - **Red = distracted**
- Final video overlays gaze point, bounding boxes, and attention status  

---

## 📈 Results Summary

- **Object Recognition Accuracy:** ~76%  
- **Eye Gaze Accuracy:** ~100% after depth adjustment  
- **Overall Distraction Detection Accuracy:** ~76%  

---

## 🗂 Repository Structure

.
├── files  
│   ├── best_def.pt  
│   ├── Eye_Gaze_def.csv  
│   └── VRS_def.vrs  
│  
├── functions.py  
├── test_video.ipynb  
└── video_flag.mp4  

---

## 🚀 Future Improvements

- Hidden Markov Model for process-stage recognition  
- More robust object detection on small components  
- Larger and more balanced datasets  
- Real-time processing when supported by Aria/MPS  
