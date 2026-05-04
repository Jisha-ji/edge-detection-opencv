# EX NO : 06 Edge-detection-opencv
## Name: JISHA BOSSNE SJ   
## Reg. No:212224230106   
 
## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

##  Program

### Developed By:
### Name: JISHA BOSSNE SJ   
### Reg. No: 212224230106

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load image
image = cv2.imread('Fish.jpg')  # replace with your path
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# ---------------- SOBEL ----------------
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=5)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=5)
sobel = cv2.magnitude(sobel_x, sobel_y)

# ---------------- PREWITT ----------------
prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

# ---------------- ROBERTS ----------------
roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

roberts_x_edge = cv2.filter2D(gray, -1, roberts_x)
roberts_y_edge = cv2.filter2D(gray, -1, roberts_y)
roberts = cv2.magnitude(roberts_x_edge.astype(np.float32),
                        roberts_y_edge.astype(np.float32))

# ---------------- LAPLACIAN ----------------
laplacian = cv2.Laplacian(gray, cv2.CV_64F)

# ---------------- CANNY ----------------
canny = cv2.Canny(gray, 50, 150)

# ---------------- DISPLAY ----------------
plt.figure(figsize=(12, 10))

plt.subplot(2, 3, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original")
plt.axis("off")

plt.subplot(2, 3, 2)
plt.imshow(sobel, cmap='gray')
plt.title("Sobel")
plt.axis("off")

plt.subplot(2, 3, 3)
plt.imshow(prewitt, cmap='gray')
plt.title("Prewitt")
plt.axis("off")

plt.subplot(2, 3, 4)
plt.imshow(roberts, cmap='gray')
plt.title("Roberts")
plt.axis("off")

plt.subplot(2, 3, 5)
plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian")
plt.axis("off")

plt.subplot(2, 3, 6)
plt.imshow(canny, cmap='gray')
plt.title("Canny")
plt.axis("off")

plt.tight_layout()
plt.show()
```
---

## Output

<img width="554" height="447" alt="image" src="https://github.com/user-attachments/assets/e6265df7-24ca-4cc4-8117-4c3df28fe583" />

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map  

<img width="559" height="468" alt="image" src="https://github.com/user-attachments/assets/baa6eca6-5b98-47bb-b359-ee76d8f09710" />

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  

<img width="567" height="460" alt="image" src="https://github.com/user-attachments/assets/b32038b9-91de-48d9-b983-069616501baa" />

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  

<img width="545" height="458" alt="image" src="https://github.com/user-attachments/assets/b1d3f569-5216-4764-b731-43eed4eec388" />

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

<img width="546" height="439" alt="image" src="https://github.com/user-attachments/assets/c0769d32-e1d2-4d84-835e-22fde6a0317b" />

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

<img width="546" height="436" alt="image" src="https://github.com/user-attachments/assets/d4355385-b587-4552-bf7f-2743e06dee50" />

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
