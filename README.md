# DIPT_EX-01 - Image-Handling-and-Pixel-Transformations-Using-OpenCV-Completion-requirements

### DEVELOPED BY : VARUN JC
### REG NO : 212224240179

## AIM :
Write a Python program using OpenCV that performs the following tasks:

1. Read and Display an Image.
2. Adjust the brightness of an image.
3. Modify the image contrast.
4. Generate a third image using bitwise operations.

## SOFTWARE REQUIRED :
```
--> Anaconda - Python 3.7
--> Jupyter Notebook (for interactive development and execution)
```
## ALGORITHM :

### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels


## PROGRAM :


1. Load an image from your local directory and display it.
```py 
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('Tamizh.jpeg', cv2.IMREAD_COLOR)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('on')  # Removes axis ticks and labels
plt.show()
```
2 . Draw a line from the top-left to the bottom-right of the image.
```py
# Load the image
image = cv2.imread('Tamizh.jpeg')

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (1064, 1279), (0, 255, 0), 10) # cv2.line(image, start_point, end_point, color, thickness)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('on')  
plt.show()

```
3. Draw a circle at the center of the image.

```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

circle_img = cv2.circle(img_rgb,(532,600),500,(0,0,255),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()

```
4. Draw a rectangle around  the whole image.
```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (1064, 1279), (255, 0, 0), 30)  # cv2.rectangle(image, start_point, end_point, color, thickness)

plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()

```

5. Add the text "OpenCV Drawing" at the top-left corner of the image.
```py
# Load the image
image = cv2.imread('ab1.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('on')  
plt.show()
```
6. Original RGB image and display it.
```py
# Load the image
image = cv2.imread('ab1.jpg') 
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("on")
```
7. Convert the image from RGB to HSV and display it.
```py
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("on")
```
8. Convert the image from RGB to GRAY and display it.
```py
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("on")
```
9. Convert the image from RGB to YCrCb and display it.
```py
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("on")
```   
10. Convert the HSV image back to RGB and display it.
```py
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("on")
```

11. Modify a block of pixels (300x300) to white, starting from (200, 200).
```py
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("on")
plt.show()

```

12. Resize the original image to half its size and display it.
```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 
image.shape

# Resize the image to half its size
resized_image = cv2.resize(image, (1280 // 2, 1065 // 2))  # (new_width, new_height)

# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("on")
plt.show()
```
13. Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

```py
# Load the image
image = cv2.imread('Tamizh.jpeg') 
image.shape

# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("on")
plt.show()
```

14.  Flip the original image horizontally and display it.
```py

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("on")

```
15. Flip the original image vertically and display it.
```py
# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("on")

```

## OUTPUT :

### 1. Original Image.

<img width="618" height="446" alt="image" src="https://github.com/user-attachments/assets/98b7ed20-b24b-4003-b688-511224a829bf" />

### 2. Image with Line.

<img width="615" height="437" alt="image" src="https://github.com/user-attachments/assets/acd24986-6cf5-492e-bbc1-e5b90d60febb" />

### 3. Image with Circle.

<img width="620" height="446" alt="image" src="https://github.com/user-attachments/assets/0363d109-c4f2-410d-99f0-72e1ec15dc1d" />


### 4. Image with Rectangle.

<img width="617" height="443" alt="image" src="https://github.com/user-attachments/assets/fb42b55b-3d0e-4288-a27c-e6cd252aee29" />


### 5. Image with Text.

<img width="620" height="442" alt="image" src="https://github.com/user-attachments/assets/20c7a9d8-7981-4464-8235-2930ef87fca7" />

### 6. Original RBG Image.

<img width="616" height="436" alt="image" src="https://github.com/user-attachments/assets/9e326368-135d-4d05-81f3-f9d7be451939" />


### 7. HSV Image .

<img width="613" height="438" alt="image" src="https://github.com/user-attachments/assets/ad210326-0cfe-4f36-8acf-84db03557efa" />



### 8. GrayScale Image.

<img width="617" height="442" alt="image" src="https://github.com/user-attachments/assets/481d3fea-7a6d-48ad-b4f4-184c7b95bde6" />


### 9. YCrCb Image.
<img width="613" height="442" alt="image" src="https://github.com/user-attachments/assets/f3565693-0fe4-47af-a2c0-6ad45d0a2ead" />


### 10. HSV to Original RGB Image.

<img width="613" height="446" alt="image" src="https://github.com/user-attachments/assets/74c40fa5-34ab-427f-9448-499f7b62481f" />


### 11. Image with White Block

<img width="617" height="438" alt="image" src="https://github.com/user-attachments/assets/22c78d5b-209a-4917-8bac-4a4f73b41231" />


### 12. Resized Image(Half Image).

<img width="617" height="441" alt="image" src="https://github.com/user-attachments/assets/dc736b34-f602-400e-8a2a-347aec9fddbf" />


### 13. Cropped Region Image .

<img width="461" height="486" alt="image" src="https://github.com/user-attachments/assets/58da0d05-179b-40d9-b82b-8aa718320bdb" />

### 14. Flipped Horizontal Image.

<img width="615" height="446" alt="image" src="https://github.com/user-attachments/assets/52393602-7a4b-4340-a323-6947aa1935e1" />
   
### 15. Flipped Vertical Image.

<img width="622" height="437" alt="image" src="https://github.com/user-attachments/assets/eaf07322-f912-4b31-96f1-1f0f4c17151b" />




## RESULT :

Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
