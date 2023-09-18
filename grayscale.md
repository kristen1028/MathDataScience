To create a random grayscale image and display it using Matplotlib, you can follow these steps:

1. Generate a random 2D array representing the grayscale pixel values.
2. Use Matplotlib to display this array as an image.

Here's a step-by-step example:

```python
import matplotlib.pyplot as plt
import numpy as np

# Generate a random 2D grayscale image (e.g., 128x128 pixels)
image_size = (128, 128)
random_image = np.random.random(image_size)  # Random values between 0 and 1

# Display the image using Matplotlib
plt.imshow(random_image, cmap='gray')  # Use a grayscale colormap
plt.axis('off')  # Hide axis numbers and ticks
plt.show()
```

In this example:
- We use NumPy to create a 2D array of random numbers between 0 and 1, which will represent the grayscale pixel values.
- We then use Matplotlib's `imshow` function to display the array as an image, specifying the grayscale colormap (`'gray'`).
- `axis('off')` is used to hide the axis numbers and ticks for a cleaner display.

This will generate a random grayscale image and display it using Matplotlib. You can adjust the `image_size` to change the dimensions of the image.
