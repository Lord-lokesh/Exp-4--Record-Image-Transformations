# Exp-4:Record-Image-Transformations
Developed By: Lokesh M
Register No: 212224230142
# Aim
To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:


Image Translation

Image Scaling

Image Shearing

Image Reflection

Image Rotation

Image Cropping
# Software Used

Anaconda – Python 3.7

Jupyter Notebook / VS Code

OpenCV (cv2)

NumPy

Matplotlib
# Algorithm
Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

Step 2:
Read the input image in color mode.

Step 3: Image Translation
Create a translation matrix to shift the image
Move the image 100 pixels to the right and 50 pixels down
Apply transformation using cv2.warpAffine()
Display original and translated images


Step 4: Image Scaling
Resize the image using scaling factors:
5.0× in x direction
2.0× in y direction
Use cv2.resize()
Display original and scaled images

Step 5: Image Shearing
Create shearing matrix
Apply shearing transformation using cv2.warpAffine()
Display original and sheared images

Step 6: Image Reflection
Perform image reflection using cv2.flip()
Display reflected image

Step 7: Image Rotation
Create rotation matrix for 45° rotation
Use cv2.getRotationMatrix2D() and cv2.warpAffine()
Display rotated image

Step 8: Image Cropping
Define crop coordinates and dimensions
Extract selected image portion using array slicing
Display cropped image
# Program

```
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 1: Load the image
image = cv2.imread('GATE EXP1.jpg')  # Load the image from file
# Display the original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert BGR to RGB for correct display
plt.title("Original Image")  
plt.axis('off') 

```

<img width="1002" height="660" alt="image" src="https://github.com/user-attachments/assets/f1c05193-24f8-4a80-a67e-dd4c1607d94d" />

```
# Step 2: Image Translation
tx, ty = 100, 50  # Translation factors (shift by 100 pixels horizontally and 50 vertically)
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  # Translation matrix: 
# [1, 0, tx] - Horizontal shift by tx
# [0, 1, ty] - Vertical shift by ty
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  # Display the translated image
plt.title("Translated Image")  
plt.axis('off')
```
<img width="1080" height="642" alt="image" src="https://github.com/user-attachments/assets/545f42eb-17b3-49f1-ab36-b4a925b99a53" />

```
# Step 3: Image Scaling
fx, fy = 5.0, 2.0  # Scaling factors (1.5x scaling for both width and height)
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
# resize: Resize the image by scaling factors fx, fy
# INTER_LINEAR: Uses bilinear interpolation for resizing
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')

```
<img width="1152" height="442" alt="image" src="https://github.com/user-attachments/assets/d078e889-13dd-4569-8f78-44e305087ab3" />

```

# Step 4: Image Shearing
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')

```
<img width="1041" height="667" alt="image" src="https://github.com/user-attachments/assets/b156cd2b-c9ec-4acf-a078-4d30e22785e5" />

```
# Step 5: Image Reflection
reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
# flip: 1 means horizontal flip, 0 would be vertical flip, -1 would flip both axes
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')
```
<img width="1040" height="592" alt="image" src="https://github.com/user-attachments/assets/f7be9321-e7db-4105-9bb9-c3d0b427bff1" />

```
# Step 6: Image Rotation
(height, width) = image.shape[:2]  # Get the image height and width
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2)  # Set the center of rotation to the image center
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  # Get the rotation matrix
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  # Apply rotation
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')

```
<img width="1207" height="676" alt="image" src="https://github.com/user-attachments/assets/14d36f83-be36-4a71-a6fc-2da0d8b23ef5" />

```
# Step 7: Image Cropping
x, y, w, h = 100, 100, 200, 150  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
# Cropping the image from coordinates (x, y) to (x+w, y+h)
cropped_image = image[y:y+h, x:x+w]
# The crop is performed by slicing the image array in the y and x directions
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')

```
<img width="1212" height="802" alt="image" src="https://github.com/user-attachments/assets/41553530-0c9e-42f9-9d92-5f1b7c7b3e84" />

# Result
Thus, various geometric transformations such as translation, scaling, shearing, reflection, rotation, and cropping are successfully performed using OpenCV.

















