# Edge-Detection-using-OpenCV

## Aim
To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required

Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm
Step 1:
Import all the necessary modules for the program.

Step 2:
Load an image using cv2.imread().

Step 3:
Convert the image to grayscale.

Step 4:
Apply Sobel operator using OpenCV to detect edges.

Step 5:
Apply Prewitt operator using custom kernels.

Step 6:
Apply Roberts operator using custom kernels.

Step 7:
Apply Laplacian operator using OpenCV.

Step 8:
Apply Canny edge detector using OpenCV.

Step 9:
Display all edge-detected images for comparison.

## Developed By
## Name: HARINI S
## Register No: 212224240049

```
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread(r"C:\Users\admin\Documents\DIPT\Q.no.6.png")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel = cv2.magnitude(sobel_x, sobel_y)
sobel = np.uint8(np.absolute(sobel))
kernelx = np.array([[1,0,-1],
                    [1,0,-1],
                    [1,0,-1]])
kernely = np.array([[1,1,1],
                    [0,0,0],
                    [-1,-1,-1]])

prewitt_x = cv2.filter2D(gray, -1, kernelx)
prewitt_y = cv2.filter2D(gray, -1, kernely)
prewitt = cv2.add(prewitt_x, prewitt_y)
roberts_x = np.array([[1,0],
                      [0,-1]])
roberts_y = np.array([[0,1],
                      [-1,0]])
roberts_x_img = cv2.filter2D(gray, -1, roberts_x)
roberts_y_img = cv2.filter2D(gray, -1, roberts_y)
roberts = cv2.add(roberts_x_img, roberts_y_img)
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = np.uint8(np.absolute(laplacian))
canny = cv2.Canny(gray, 100, 200)
plt.figure(figsize=(12,10))
plt.subplot(3,3,1)
plt.imshow(gray, cmap='gray')
plt.title("Original Grayscale")
plt.axis('off')
plt.subplot(3,3,2)
plt.imshow(sobel, cmap='gray')
plt.title("Sobel Edge")
plt.axis('off')
plt.subplot(3,3,3)
plt.imshow(prewitt, cmap='gray')
plt.title("Prewitt Edge")
plt.axis('off')
plt.subplot(3,3,4)
plt.imshow(roberts, cmap='gray')
plt.title("Roberts Edge")
plt.axis('off')
plt.subplot(3,3,5)
plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian Edge")
plt.axis('off')
plt.subplot(3,3,6)
plt.imshow(canny, cmap='gray')
plt.title("Canny Edge")
plt.axis('off')
plt.tight_layout()
plt.show()
```

## Output
<img width="261" height="177" alt="image" src="https://github.com/user-attachments/assets/9db5d6dd-e796-482a-83c2-6a9548d9da76" /><br>
<img width="205" height="175" alt="image" src="https://github.com/user-attachments/assets/485bcd36-1f90-4430-b4d3-3165b4cf8759" /><br>
<img width="222" height="173" alt="image" src="https://github.com/user-attachments/assets/e442bf01-bb66-4d1f-b007-120cf6fd3226" /><br>
<img width="219" height="172" alt="image" src="https://github.com/user-attachments/assets/17acda72-7f7a-44a1-aa0c-e334ff68356f" /><br>
<img width="240" height="174" alt="image" src="https://github.com/user-attachments/assets/03882ada-93c6-4840-9f42-7972808e7447" /><br>
<img width="269" height="175" alt="image" src="https://github.com/user-attachments/assets/9d81ede4-1243-458e-85c1-92c6999290f3" /><br>

## Result
Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.








