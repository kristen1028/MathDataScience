To plot a line given by the equation \(y = mx + b\) in Python using Matplotlib, you'll first need to generate the \(x\) values, compute the corresponding \(y\) values using the equation, and then create a plot. Here's a step-by-step example:

```python
import matplotlib.pyplot as plt
import numpy as np

# Parameters for the line equation y = mx + b
m = 2  # Slope
b = 3  # Intercept

# Generate x values
x = np.linspace(-10, 10, 100)  # 100 points between -10 and 10

# Compute y values using the equation y = mx + b
y = m * x + b

# Create the plot
plt.plot(x, y, label='y = {}x + {}'.format(m, b))

# Add labels and title
plt.xlabel('x')
plt.ylabel('y')
plt.title('Plot of y = {}x + {}'.format(m, b))

# Add a legend
plt.legend()

# Display the plot
plt.grid(True)
plt.show()
```

In this example:
- We set the parameters \(m\) and \(b\) for the line equation \(y = mx + b\).
- We generate a range of \(x\) values using NumPy's `linspace` function, which creates 100 evenly spaced points between -10 and 10.
- We compute the corresponding \(y\) values using the line equation \(y = mx + b\).
- We use Matplotlib's `plot` function to plot \(x\) against \(y\) and label the line with the equation.
- Labels, title, legend, and grid are added to the plot to enhance its readability.

Run this code to plot a line based on the given equation \(y = mx + b\). You can adjust the values of \(m\) and \(b\) to plot different lines.
