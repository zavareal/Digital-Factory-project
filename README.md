Requisites:

install ultralytics library (!pip install ultralytics)

install aria studio libraries (!pip install projectaria-tools'[all]' or !pip install projectaria-tools)


files->

    best_def.pt: the object detection model

    Eye_Gaze_def.csv: the csv file of the eye gaze observation given by MPS

    VRS_def.vrs: the corrisponding vrs file

functions.py: a python file containing functions that notebook will call. The functions are descripted inside the file and in the report

test_video.ipynb: the notebook that will process the VRS

video_flag.mp4: the video output of the notebook


Steps:

1. run the test_video.ipynb code

2. video will be saved by default on video_flag.mp4 (the output name can be changed with output_video_path attribute when calling the inference_video function) 
