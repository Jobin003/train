!nvidia-smi
!pip install ultralytics
from ultralytics import YOLO
model = YOLO("yolov8m.pt")
import os
from IPython.display import display, Image
from IPython import display
import kagglehub

# Download the latest version of the dataset
path = kagglehub.dataset_download("mehmetcubukcu/weapon-detection")

# Print the path to the downloaded dataset files
print("Path to dataset files:", path)

# Optional: Move the dataset to the current folder
import shutil
import os

# Define the target folder in the current directory
target_folder = "./content"

# Move dataset to the current folder if it's not already there
if not os.path.exists(target_folder):
    shutil.move(path, target_folder)
    print(f"Dataset moved to: {target_folder}")
else:
    print(f"Dataset already exists at: {target_folder}")
!yolo task=detect mode=train model=yolov8m.pt data=/content/weapon-detection/data.yaml epochs=30 imgsz=640
