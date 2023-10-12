# Import necessary libraries and modules
import numpy as np
import matplotlib.pyplot as plt
import base64
from io import BytesIO
from scipy.signal import convolve2d
from skimage import data, color, io
import IPython
from torchvision import datasets
from skimage.util import montage
import wandb as wb
from skimage.io import imread
from skimage.transform import resize

# Define a function to plot an image
def plot(x):
    fig, ax = plt.subplots()
    im = ax.imshow(x, cmap='gray')
    ax.axis('off')
    fig.set_size_inches(5, 5)
    plt.show()

# Load an RGB image from a URL and display it
image = io.imread("https://th.bing.com/th/id/OIP.himN5x0Zvru00xUdk3p55QHaE8?pid=ImgDet&rs=1")
image = image[:, :, :]  # Keep all color channels
plot(image)  # Display the image

# Resize the image to 224x224 and display the resized image
image_resize = resize(image, (224, 224))
plot(image_resize)  # Display the resized image

# Convert the resized image to grayscale and display it
image_gray = np.mean(image_resize, axis=2)
plot(image_gray)  # Display the grayscale image

# Define a convolution filter 'a'
a = np.matrix([[-1, -1, -1], [-1, 8, -1], [-1, -1, -1]])

# Convolve the grayscale image with the filter 'a' and display the results
x = image_gray
x2 = conv2(x, a)
plot(x)
plot(x2)

# Define a function for 2D convolution
def conv2(x, f):
    x2 = np.zeros(x.shape)
    for i in range(1, x.shape[0] - 1):
        for j in range(1, x.shape[1] - 1):
            x2[i, j] = (
                f[0, 0] * x[i - 1, j - 1]
                + f[0, 1] * x[i - 1, j]
                + f[0, 2] * x[i - 1, j + 1]
                + f[1, 0] * x[i, j - 1]
                + f[1, 1] * x[i, j]
                + f[1, 2] * x[i, j + 1]
                + f[2, 0] * x[i + 1, j - 1]
                + f[2, 1] * x[i + 1, j]
                + f[2, 2] * x[i + 1, j + 1]
            )
    return x2

# Apply convolution with 10 random filters and display the results
for i in range(10):
    a = 2 * np.random.random((3, 3)) - 1
    print(a)
    z = conv2(x, a)
    plot(z)

# Load an RGB image from a URL and convert it to grayscale
img_url = "https://th.bing.com/th/id/OIP.himN5x0Zvru00xUdk3p55QHaE8?pid=ImgDet&rs=1"
img = io.imread(img_url)
x = color.rgb2gray(img)

# Apply convolution with 10 more random filters and display the results
for i in range(10):
    a = 2 * np.random.random((3, 3)) - 1
    print(a)
    z = convolve2d(x, a, mode='valid')  # 2D convolution
    plot(z)
