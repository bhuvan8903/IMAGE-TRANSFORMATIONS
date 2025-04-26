# IMAGE-TRANSFORMATIONS


## Aim
To perform image transformation such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping using OpenCV and Python.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Import all the necessary modules  

### Step2:
Choose an image and save it as filename.jpg

### Step3:
Use imread to read the image

### Step4:
Use cv2.warpPerspective(image,M,(cols,rows)) to translation the image

### Step5:
Use cv2.warpPerspective(image,M,(cols2,rows2)) to scale the image

### Step6:
Use cv2.warpPerspective(image,M,(int(cols1.5),int(rows1.5))) for x and y axis to shear the image

### Step7:
Use cv2.warpPerspective(image,M,(int(cols),int(rows))) for x and y axis to reflect the image

### Step8:
Use cv2.warpPerspective(image,M,(int(cols),int(rows))) to rotate the image

### Step9:
Crop the image to remove unwanted areas from an image

### Step10:
Use cv2.imshow to show the image

### Step11:
End the program

## Program:
```python
Developed By: Bhuvaneshwaran H
Register Number:212223240018
import numpy as np
import cv2
import matplotlib.pyplot as plt

# i) Image Translation
input_img = cv2.imread("color image of flower.jpg")
input_img = cv2.cvtColor(input_img, cv2.COLOR_BGR2RGB)  # Convert BGR to RGB for correct display
plt.axis('off')
plt.imshow(input_img)
plt.title("Original Image")
plt.show()

rows, cols, dim = input_img.shape

# Translation matrix
M = np.float32([[1, 0, 20],    # shift 20 pixels right
                [0, 1, 50]])   # shift 50 pixels down

translated_img = cv2.warpAffine(input_img, M, (cols, rows))
plt.axis('off')
plt.imshow(translated_img)
plt.title("Translated Image")
plt.show()


# ii) Image Scaling
scaled_img = cv2.resize(input_img, None, fx=1.5, fy=1.5, interpolation=cv2.INTER_LINEAR)
plt.axis('off')
plt.imshow(scaled_img)
plt.title("Scaled Image")
plt.show()


# iii) Image Shearing
# Shearing along x-axis
M_x = np.float32([[1, 0.2, 0],
                  [0, 1, 0],
                  [0, 0, 1]])

# Shearing along y-axis
M_y = np.float32([[1, 0, 0],
                  [0.2, 1, 0],
                  [0, 0, 1]])

# Convert perspective matrices to 3x3 for warpPerspective
sheared_img_xaxis = cv2.warpPerspective(input_img, M_x, (int(cols * 1.5), rows))
sheared_img_yaxis = cv2.warpPerspective(input_img, M_y, (cols, int(rows * 1.5)))

plt.axis('off')
plt.imshow(sheared_img_xaxis)
plt.title("Sheared Image (X-Axis)")
plt.show()

plt.axis('off')
plt.imshow(sheared_img_yaxis)
plt.title("Sheared Image (Y-Axis)")
plt.show()

# iv) Image Reflection
input_image = cv2.imread("got.jpg")
input_image = cv2.cvtColor(input_image, cv2.COLOR_BGR2RGB)
plt.axis("off")
plt.imshow(input_image)
plt.title("Original Image")
plt.show()

rows, cols, dim = input_image.shape

# Reflection across the X-axis (flip vertically)
M_x = np.float32([[1, 0, 0],
                  [0, -1, rows],
                  [0, 0, 1]])

# Reflection across the Y-axis (flip horizontally)
M_y = np.float32([[-1, 0, cols],
                  [0, 1, 0],
                  [0, 0, 1]])

reflected_img_xaxis = cv2.warpPerspective(input_image, M_x, (cols, rows))
reflected_img_yaxis = cv2.warpPerspective(input_image, M_y, (cols, rows))

plt.axis('off')
plt.imshow(reflected_img_xaxis)
plt.title("Reflected Image (X-Axis)")
plt.show()

plt.axis('off')
plt.imshow(reflected_img_yaxis)
plt.title("Reflected Image (Y-Axis)")
plt.show()


# v) Image Rotation
input_image = cv2.imread("got.jpg")
input_image = cv2.cvtColor(input_image, cv2.COLOR_BGR2RGB)

rows, cols, dim = input_image.shape
angle = np.radians(45)  # 45 degrees in radians

# Rotation matrix
M = np.float32([[np.cos(angle), -np.sin(angle), 0],
                [np.sin(angle), np.cos(angle), 0],
                [0, 0, 1]])

rotated_img = cv2.warpPerspective(input_image, M, (cols, rows))

plt.axis('off')
plt.imshow(rotated_img)
plt.title("Rotated Image (45 degrees)")
plt.show()


# vi) Image Cropping
input_image = cv2.imread("got.jpg")
input_image = cv2.cvtColor(input_image, cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.title("Original Image for Cropping")
plt.show()

# Cropping (example: taking center region)
start_row, start_col = int(rows * 0.25), int(cols * 0.25)
end_row, end_col = int(rows * 0.75), int(cols * 0.75)

cropped_img = input_image[start_row:end_row, start_col:end_col]

plt.axis('off')
plt.imshow(cropped_img)
plt.title("Cropped Image")
plt.show()



```
## Output:
### Input image:
![image](https://github.com/user-attachments/assets/15af71a8-d45b-4f13-98de-a4d21f35392c)

### i)Image Translation

![image](https://github.com/user-attachments/assets/076d48a8-a8ec-4ac7-a838-92aae94f0af3)

### ii) Image Scaling
![image](https://github.com/user-attachments/assets/3d177d24-f021-4462-bc05-3313f0d0c492)


### iii)Image shearing

![image](https://github.com/user-attachments/assets/237565e7-036f-4aa4-b321-7a970cb442ac)
![image](https://github.com/user-attachments/assets/4be4015a-8836-4c02-99b2-80bf39894f5b)


### iv)Image Reflection

![image](https://github.com/user-attachments/assets/a9f8fd08-417e-43cc-a240-b60109c03673)
![image](https://github.com/user-attachments/assets/a7ac47d5-9ef4-47cc-a7ee-0ebaf9cd2f37)


### v)Image Rotation
![image](https://github.com/user-attachments/assets/7338decc-1c0b-464b-871c-cac0f333250c)




### vi)Image Cropping
![image](https://github.com/user-attachments/assets/32334afc-cb76-4388-8b55-17c515ddb5a0)





## Result: 

Thus the different image transformations such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping are done using OpenCV and python programming.
