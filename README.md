# Canny-Edge-Detection

## Aim:
To implement the Canny Edge Detection algorithm using Python and OpenCV to perform noise reduction, gradient calculation, and hysteresis thresholding to extract sharp, single-pixel structural boundaries from an image.

## Algorithm:
```
1) Image Reading: Load the source color image into the environment using cv2.imread().
2) Grayscale Conversion: Convert the image from BGR to Grayscale using cv2.cvtColor() to simplify the pixel intensity calculations.
3) Noise Reduction: Apply a Gaussian Filter (typically $5 \times 5$ kernel) to smooth the image and prevent pixel noise from being detected as false edges.
4) Gradient Calculation: Use Sobel kernels to find the intensity gradients in both horizontal ($G_x$) and vertical ($G_y$) directions.
5) Non-Maximum Suppression (NMS): Thin out the detected edges by suppressing all gradient values that are not local maxima in the direction of the gradient.
6) Hysteresis Thresholding: Apply two threshold values ($T_1$ and $T_2$): Pixels with gradients $> T_2$ are marked as strong edges.Pixels with gradients between $T_1$ and $T_2$ are marked as weak edges (preserved only if connected to a strong edge). Pixels $< T_1$ are suppressed.
7) Visualization: Display the original image and the final edge map using matplotlib.
```

## Program:
```
NAME: OVIYA N
REG.NO: 212223040140
```
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# 1. Load the sample image and convert it to grayscale
image = cv2.imread('Fish.jpg')  
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# 2. Apply Gaussian Blur to reduce noise before edge tracking
blurred = cv2.GaussianBlur(gray, (5, 5), 0)

# 3. Apply Canny Edge Detector with baseline thresholds (50, 150)
canny_edges = cv2.Canny(blurred, 50, 150)

# 4. Display the Results Side-by-Side
plt.figure(figsize=(12, 6))

# Original Image
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image (Fish.jpg)")
plt.axis("off")

# Canny Edge Map
plt.subplot(1, 2, 2)
plt.imshow(canny_edges, cmap='gray')
plt.title("Canny Edge Detection")
plt.axis("off")

plt.tight_layout()
plt.show()
```
## Output:
<img width="1026" height="419" alt="image" src="https://github.com/user-attachments/assets/10532328-2221-4e58-9e00-05fe360e9870" />


## Result:
The Canny Edge Detection pipeline was successfully implemented in Python using the OpenCV library and verified on the sample image.
