# Exp 4 - Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By: Deepak K R  

### Register No: 212225040057

---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

<img width="740" height="437" alt="Screenshot 2026-08-08 224637" src="https://github.com/user-attachments/assets/7a3c2d1c-b463-4fac-bd60-31d5a39dd2d5" />


### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

<img width="1100" height="426" alt="Screenshot 2026-08-08 224645" src="https://github.com/user-attachments/assets/c74c05b3-99d9-4367-8a95-429a3e344c68" />


### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

<img width="1092" height="435" alt="Screenshot 2026-08-08 224656" src="https://github.com/user-attachments/assets/61574775-8dcb-4b4a-aabd-88cfda5e6a03" />


### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

<img width="1096" height="325" alt="Screenshot 2026-08-08 224705" src="https://github.com/user-attachments/assets/ae131b22-7502-4d53-b0a6-0d66e5cdfc73" />


### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

<img width="1105" height="427" alt="Screenshot 2026-08-08 224713" src="https://github.com/user-attachments/assets/d4fc95f5-cc3e-440d-baf5-b663c586a9a8" />

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
