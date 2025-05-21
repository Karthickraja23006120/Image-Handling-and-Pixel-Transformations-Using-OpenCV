# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
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

## Program Developed By:
- **Name:** Karthick Raja K
- **Register Number:** 212223240066

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
img = cv2.imread('Eagle_in_Flight.jpg', cv2.IMREAD_GRAYSCALE)
```

#### 2. Print the image width, height & Channel.
```
image = cv2.imread('Eagle_in_Flight.jpg')
print("Height, Width and Channel:", image.shape)
```
![image](https://github.com/user-attachments/assets/258d15fb-a5d3-4d07-b67e-1f8c9e64db84)

#### 3. Display the image using matplotlib imshow().
```
import matplotlib.pyplot as plt
plt.imshow(img)
```
![image](https://github.com/user-attachments/assets/248198e2-7598-4323-a575-3b32ccc2d8ed)

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
cv2.imwrite('Eagle_in_Flight.png', image)
```
![image](https://github.com/user-attachments/assets/59335054-91e0-41d9-abce-679d2c5097f0)

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
img = cv2.imread('Eagle_in_Flight.png')
color_img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(color_img)
```
![image](https://github.com/user-attachments/assets/7f304c71-3c88-4368-8de6-12b07be1aa06)


#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
plt.imshow(color_img)
color_img.shape
```
![image](https://github.com/user-attachments/assets/2fcaf6e0-6630-4838-a7b6-6de4cc04917d)

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
cropped = color_img[10:450, 150:570]
plt.imshow(cropped)
plt.axis("off")
```
![image](https://github.com/user-attachments/assets/7fb4ba33-12b4-48c1-81a8-7387e6e8b2e5)

#### 8. Resize the image up by a factor of 2x.
```
height, width = image.shape[:2]
resized_image = cv2.resize(image, (width * 2, height * 2), interpolation=cv2.INTER_LINEAR)
plt.imshow(resized_image)
```
![image](https://github.com/user-attachments/assets/5241e08c-0c75-404f-928e-7475e90cf194)

#### 9. Flip the cropped/resized image horizontally.
```
flipped = cv2.flip(resized_image, 1)
plt.imshow(flipped)
```
![image](https://github.com/user-attachments/assets/bbd0a738-6dfd-47c5-b6d0-a9f138fefcba)

#### 10. Read in the image ('Apollo-11-launch.jpg').
```
img_apollo = cv2.imread('Apollo-11-launch.jpg')
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
cv2.putText(img_apollo, 'Apollo 11 Saturn V Launch, July 16, 1969', (50, img_apollo.shape[0] - 50), cv2.FONT_HERSHEY_PLAIN, 2, (255, 255, 255), 2)
plt.imshow(img_apollo)
```
![image](https://github.com/user-attachments/assets/05e84c2f-0da0-4069-9ef1-eecd83320252)

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
cv2.rectangle(img_apollo, (400, 30), (750, 600), (255, 0, 255), 3)
```
![image](https://github.com/user-attachments/assets/8f43db89-6602-4504-8d00-36fcd57225d6)

#### 13. Display the final annotated image.
```
plt.imshow(img_apollo)
```
![image](https://github.com/user-attachments/assets/33c9d80a-04c7-4231-abe9-f17c6223bdd6)

#### 14. Read the image ('Boy.jpg').
```
boy_img = cv2.imread('Boy.jpg')
```

#### 15. Adjust the brightness of the image.
```
# Create a matrix of ones (with data type float64)
import numpy as np
matrix_ones = np.ones(boy_img.shape, dtype='uint8') * 50
```

#### 16. Create brighter and darker images.
```
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(10, 3))
for i, img in enumerate([boy_img, img_darker, img_brighter]):
    plt.subplot(1, 3, i + 1)
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.show()
```
![image](https://github.com/user-attachments/assets/684814b5-a82f-47c8-a4ed-d8af127ddca3)

#### 18. Modify the image contrast.
```
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
matrix1 = np.ones(boy_img.shape, dtype='uint8') * 25
matrix2 = np.ones(boy_img.shape, dtype='uint8') * 50
img_higher1 = cv2.addWeighted(boy_img, 1.1, matrix1, 0, 0)
img_higher2 = cv2.addWeighted(boy_img, 1.2, matrix2, 0, 0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.figure(figsize=(10, 3))
for i, img in enumerate([boy_img, img_higher1, img_higher2]):
    plt.subplot(1, 3, i + 1)
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.show()
```
![image](https://github.com/user-attachments/assets/94b69058-4172-487e-8de0-a270f928d9dd)

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```
b, g, r = cv2.split(boy_img)
plt.figure(figsize=(10, 3))
for i, channel in enumerate([b, g, r]):
    plt.subplot(1, 3, i + 1)
    plt.imshow(channel, cmap='gray')
plt.show()
```
![image](https://github.com/user-attachments/assets/691841de-c5be-4c1b-8271-3f4c4159962a)

#### 21. Merged the R, G, B , displays along with the original image
```
merged = cv2.merge([b, g, r])
plt.imshow(cv2.cvtColor(merged, cv2.COLOR_BGR2RGB))
plt.show()
```
![image](https://github.com/user-attachments/assets/8da4a5a7-4aa1-4e3d-8efb-5ac7c857729f)

#### 22. Split the image into the H, S, V components & Display the channels.
```
hsv = cv2.cvtColor(boy_img, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)
plt.figure(figsize=(10, 3))
for i, channel in enumerate([h, s, v]):
    plt.subplot(1, 3, i + 1)
    plt.imshow(channel, cmap='gray')
plt.show()
```
![image](https://github.com/user-attachments/assets/5f7587fe-5a1b-4d3c-9161-8e59967243d0)

#### 23. Merged the H, S, V, displays along with original image.
```
#merged_hsv = cv2.merge([h, s, v])
plt.imshow(cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB))
plt.show()
```
![image](https://github.com/user-attachments/assets/7b48268d-b78b-43fa-9ffc-99f432a8843c)

## Output:
- **i)** Read and Display an Image.
- ![image](https://github.com/user-attachments/assets/6267b003-5a8c-4bf9-aa61-86d7b292b538)
  
- **ii)** Adjust Image Brightness.
- ![image](https://github.com/user-attachments/assets/5fc7e17a-4e5a-4aa6-a264-6fcb44e50685)

- **iii)** Modify Image Contrast.
- ![image](https://github.com/user-attachments/assets/a2c76019-db07-4d97-9113-03d51f24afb1)

- **iv)** Generate Third Image Using Bitwise Operations.
- ![image](https://github.com/user-attachments/assets/f8c12be8-8c77-4fee-8f04-8c6555c3db1f)


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

