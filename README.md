# IPMVLB
**#    EXPT No.1**
import cv2
from google.colab.patches import cv2_imshow
import numpy as np
import matplotlib.pyplot as plt
image1 = cv2.imread('input1.jpg')
image2 = cv2.imread('input2.jpg')
img1= cv2.resize(image1, (200, 250))
img2= cv2.resize(image2, (200, 250))
cv2_imshow(image1)
cv2_imshow(image2)
add = img1+img2
sub = img1-img2
mul = img1*img2
div = img1/img2
plt.subplot(2, 2, 1)
plt.imshow(add)
plt.title('Addition')
plt.axis('off')
plt.subplot(2, 2, 2)
plt.imshow(sub)
plt.title('Subtraction')
plt.axis('off')
plt.subplot(2, 2, 3)
plt.imshow(mul)
plt.title('Multiplication')
plt.axis('off')
plt.subplot(2, 2, 4)
plt.imshow(div)
plt.title('Division')
plt.axis('off')
plt.tight_layout()
plt.show()

**# EXPT NO 2A**
import cv2
import matplotlib.pyplot as plt
image = cv2.imread('negative.jpg')
negative_image = 255 - image
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
negative_rgb = cv2.cvtColor(negative_image, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(8,4))
plt.subplot(1,2,1)
plt.title("Original Image")
plt.imshow(image_rgb)
plt.axis('off')

**# EXPT NO 2A**
# Digital Negative image (with binary image)
import cv2
import matplotlib.pyplot as plt
image = cv2.imread('blackwhite.avif')
negative_image = 255 - image
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
negative_rgb = cv2.cvtColor(negative_image, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(8,4))
plt.subplot(1,2,1)
plt.title("Original Image")
plt.imshow(image_rgb)
plt.axis('off')
plt.subplot(1,2,2)
plt.title("Color Negative Image")
plt.imshow(negative_rgb)
plt.axis('off')
plt.show()

**# EXPT NO 2B**
# Bit Plane Slicing
import cv2
import matplotlib.pyplot as plt
img = cv2.imread('flower.jpg', 0)
for i in range(8):
    bit_plane = (img >> i) & 1
    plt.subplot(2, 4, i+1)
    plt.imshow(bit_plane, cmap='gray')
    plt.title(f'Bit {i}')
    plt.axis('off')
plt.show()

**# EXPT NO.3**
# To separate RGB components from color image
!pip install cv
import cv2
from google.colab.patches import cv2_imshow
import numpy as np
from PIL import Image
import matplotlib.pyplot as plt
image = cv2.imread('flower.jpg')
img= cv2.resize(image, (250, 200))
red,green,blue = cv2.split(img)
zeros = np.zeros(blue.shape, np.uint8)
redBGR = cv2.merge([red,zeros,zeros])
greenBGR = cv2.merge([zeros,green,zeros])
blueBGR = cv2.merge([zeros,zeros,blue])
Titles =["Original", "Red", "Green", "Blue"]
images =[img, redBGR, greenBGR, blueBGR]
count = 4
for i in range(count):
    plt.subplot(2, 2, i + 1)
    plt.axis("off")
    plt.title(Titles[i])
    plt.imshow(images[i])
plt.show()
