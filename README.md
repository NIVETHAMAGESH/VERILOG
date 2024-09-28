# PYTHON-WORKSHOP

from ultralytics import YOLO
import cv2

model = YOLO("best.pt")
results = model.predict(source=0, conf=0.85, show=True)
