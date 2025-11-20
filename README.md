# Image-sketch-converter
This project converts normal images into pencil sketches using OpenCV.

import cv2

# Load image
img = cv2.imread("sample.jpg")

# Convert to gray
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Blur the image
blur = cv2.GaussianBlur(gray, (21, 21), 0)

# Dodge technique for sketch effect
def dodge(x, y):
    return cv2.divide(x, 255 - y, scale=256)

sketch = dodge(gray, blur)

# Save output
cv2.imwrite("sketch_output.jpg", sketch)

print("Sketch created successfully!")
