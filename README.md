# Exp 4 - Geometric Transformations Using OpenCV

### Developed By: Deepak K R  

### Register No: 212225040057

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

```py
# Step 1: Import the required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Read the input image in color mode
# Using verbatim file name "feather.jpg"
img_bgr = cv2.imread("feather.jpg")

# Convert from BGR (OpenCV default) to RGB (for Matplotlib display)
img = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB)

# Get image dimensions (rows, columns)
rows, cols, channels = img.shape

# Helper function to plot images easily throughout the program
def show_images(titles, images, figsize=(10, 5)):
    plt.figure(figsize=figsize)
    for i in range(len(images)):
        plt.subplot(1, len(images), i + 1)
        plt.imshow(images[i])
        plt.title(titles[i])
        plt.axis('off')
    plt.show()
```

```py
# Step 3: Image Translation
# Translation matrix: [[1, 0, tx], [0, 1, ty]]
# tx = 50 (right), ty = 80 (down)
M_translate = np.float32([[1, 0, 50], [0, 1, 80]])

# Apply transformation
translated_img = cv2.warpAffine(img, M_translate, (cols, rows))

# Display original and translated images
show_images(['Original Image', 'Translated (Right: 50, Down: 80)'], [img, translated_img])
```

```py
# Step 4: Image Scaling
# Resize to 0.5x (downscale)
img_downscaled = cv2.resize(img, None, fx=0.5, fy=0.5, interpolation=cv2.INTER_LINEAR)

# Resize to 2x (upscale)
img_upscaled = cv2.resize(img, None, fx=2.0, fy=2.0, interpolation=cv2.INTER_LINEAR)

# Display original, downscaled, and upscaled images
show_images(['Original', 'Downscaled (0.5x)', 'Upscaled (2x)'], 
            [img, img_downscaled, img_upscaled], figsize=(15, 5))
```

```py
# Step 5: Image Shearing
shear_factor = 0.2

# Horizontal shearing matrix
M_shear_h = np.float32([
    [1, shear_factor, 0],
    [0, 1, 0]
])
# We add extra width to avoid cropping the sheared image
sheared_h_img = cv2.warpAffine(img, M_shear_h, (cols + int(shear_factor * rows), rows))

# Vertical shearing matrix
M_shear_v = np.float32([
    [1, 0, 0],
    [shear_factor, 1, 0]
])
# We add extra height to avoid cropping
sheared_v_img = cv2.warpAffine(img, M_shear_v, (cols, rows + int(shear_factor * cols)))

# Display original and sheared images
show_images(['Original', 'Horizontally Sheared', 'Vertically Sheared'], 
            [img, sheared_h_img, sheared_v_img], figsize=(15, 5))
```

```py
# Step 6: Image Reflection
# Horizontal reflection (flipCode = 1)
flip_horizontal = cv2.flip(img, 1)

# Vertical reflection (flipCode = 0)
flip_vertical = cv2.flip(img, 0)

# Both axes reflection (flipCode = -1)
flip_both = cv2.flip(img, -1)

# Display all reflected images
show_images(['Original', 'Horizontal Flip', 'Vertical Flip', 'Both Axes Flip'], 
            [img, flip_horizontal, flip_vertical, flip_both], figsize=(20, 5))
```

```py
# Step 7: Image Rotation
center = (cols // 2, rows // 2)

# Create rotation matrix for 45 degrees
M_rot_45 = cv2.getRotationMatrix2D(center, 45, 1.0)
rotated_45_img = cv2.warpAffine(img, M_rot_45, (cols, rows))

# Create rotation matrix for 90 degrees
M_rot_90 = cv2.getRotationMatrix2D(center, 90, 1.0)
rotated_90_img = cv2.warpAffine(img, M_rot_90, (cols, rows))

# Display original and rotated images
show_images(['Original', '45° Rotation', '90° Rotation'], 
            [img, rotated_45_img, rotated_90_img], figsize=(15, 5))
```

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
