# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

### Step1:
Load the input image using cv2.imread() and convert it to a grayscale image using cv2.cvtColor() with the color conversion code cv2.COLOR_BGR2GRAY.

### Step2:
Use a fixed threshold value (e.g., 127) for global thresholding with cv2.threshold(). Pixels with intensity above this value are set to maximum intensity (255), and the rest are set to minimum intensity (0).

### Step3:
Use adaptive thresholding, which calculates the threshold for smaller regions of the image. The threshold is calculated dynamically using cv2.adaptiveThreshold() with the ADAPTIVE_THRESH_GAUSSIAN_C method.

### Step4:
Otsu's method automatically finds an optimal threshold value by minimizing the within-class variance. Apply it using cv2.threshold() with the flag cv2.THRESH_OTSU.

### Step5:
Use plt.imshow() to visualize the grayscale image and the segmented images from global, adaptive, and Otsu's thresholding techniques.

## Program

```
import cv2
import matplotlib.pyplot as plt
```  
```
image = cv2.imread('zoro.jpeg')
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```
```
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.xticks([]), plt.yticks([])
plt.show()

```
![image](https://github.com/user-attachments/assets/ffab563f-f31c-4c6f-8b9a-f9dd78505400)

```
ret_global, th_global = cv2.threshold(gray_image, 127, 255, cv2.THRESH_BINARY)
```
```
plt.imshow(th_global, cmap='gray')
plt.title('Global Thresholding (v=127)')
plt.xticks([]), plt.yticks([])
plt.show()
```
![image](https://github.com/user-attachments/assets/1ae8561b-392a-46e0-8e56-d828d6c6879b)

```
th_adaptive = cv2.adaptiveThreshold(gray_image, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
                                    cv2.THRESH_BINARY, 11, 2)
```
```
plt.imshow(th_adaptive, cmap='gray')
plt.title('Adaptive Gaussian Thresholding')
plt.xticks([]), plt.yticks([])
plt.show()

```
![image](https://github.com/user-attachments/assets/a9c482c0-b871-424c-bcfb-e0a9e60fd4da)

```
ret_otsu, th_otsu = cv2.threshold(gray_image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)
```
```
plt.imshow(th_otsu, cmap='gray')
plt.title("Otsu's Thresholding")
plt.xticks([]), plt.yticks([])
plt.show()

```
![image](https://github.com/user-attachments/assets/050ee586-49a8-4a20-862e-a098e45c015e)

## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
