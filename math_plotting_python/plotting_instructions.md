# Plotting Mathematical Equations with Python

## Learning Objectives
- Understand how to create coordinate points for plotting
- Plot linear, quadratic, and trigonometric functions
- Customize plots with labels, grids, and multiple functions
- Explore parametric equations for circles and ellipses

---

## Setup: Import Required Libraries

First, we need to import the libraries we'll use:
- `numpy`: for creating arrays of numbers and mathematical operations
- `matplotlib.pyplot`: for creating plots

```python
import numpy as np
import matplotlib.pyplot as plt

# This makes plots appear in the notebook
%matplotlib inline
```

---

## Part 1: Linear Functions (y = mx + b)

### Understanding the Process
To plot any function, we need to:
1. Create an array of x-values (our input)
2. Calculate corresponding y-values using our equation
3. Plot the (x, y) coordinate pairs

### Example 1: Plot y = 2x + 3

```python
# Step 1: Create x-values from -10 to 10
# np.linspace(start, stop, number_of_points)
x = np.linspace(-10, 10, 100)

# Step 2: Calculate y-values
y = 2 * x + 3

# Step 3: Create the plot
plt.figure(figsize=(8, 6))
plt.plot(x, y, 'b-', linewidth=2, label='y = 2x + 3')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Linear Function')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)  # x-axis
plt.axvline(x=0, color='k', linewidth=0.5)  # y-axis
plt.legend()
plt.show()
```

### Exercise 1: Your Turn!

Plot the following linear functions:
1. y = -3x + 5
2. y = 0.5x - 2

Try changing the slope and y-intercept to see how the line changes!

```python
# Your code here
x = np.linspace(-10, 10, 100)

# Calculate y-values for your equation
y = # YOUR EQUATION HERE

# Create your plot
```

### Plotting Multiple Functions Together

Let's compare different linear functions on the same graph.

```python
# Comparing three linear functions
x = np.linspace(-10, 10, 100)

y1 = 2 * x + 3
y2 = -x + 1
y3 = 0.5 * x - 2

plt.figure(figsize=(10, 6))
plt.plot(x, y1, 'b-', linewidth=2, label='y = 2x + 3')
plt.plot(x, y2, 'r-', linewidth=2, label='y = -x + 1')
plt.plot(x, y3, 'g-', linewidth=2, label='y = 0.5x - 2')

plt.xlabel('x', fontsize=12)
plt.ylabel('y', fontsize=12)
plt.title('Comparing Linear Functions', fontsize=14)
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)
plt.axvline(x=0, color='k', linewidth=0.5)
plt.legend(fontsize=10)
plt.show()
```

---

## Part 2: Quadratic Functions (y = ax² + bx + c)

Quadratic functions create parabolas - curved shapes that are fundamental in physics and mathematics.

### Example: Plot y = x² - 4x + 3

```python
x = np.linspace(-2, 6, 200)
y = x**2 - 4*x + 3

plt.figure(figsize=(8, 6))
plt.plot(x, y, 'purple', linewidth=2, label='y = x² - 4x + 3')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Quadratic Function (Parabola)')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)
plt.axvline(x=0, color='k', linewidth=0.5)
plt.legend()
plt.show()
```

### Exercise 2: Quadratic Functions

Plot these quadratic functions:
1. y = -x² + 2x + 1 (opens downward)
2. y = 2x² - 3x - 5

Notice how the coefficient of x² affects the parabola's direction and width!

```python
# Your code here
x = np.linspace(-5, 5, 200)

# Calculate y-values


# Create your plot
```

---

## Part 3: Trigonometric Functions

Sine and cosine functions create wave patterns. These are crucial in physics, engineering, and signal processing.

### Plot Sine and Cosine Functions

```python
# Create x-values from 0 to 2π (two full periods)
x = np.linspace(0, 2*np.pi, 200)

y_sin = np.sin(x)
y_cos = np.cos(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y_sin, 'b-', linewidth=2, label='y = sin(x)')
plt.plot(x, y_cos, 'r-', linewidth=2, label='y = cos(x)')

plt.xlabel('x (radians)')
plt.ylabel('y')
plt.title('Trigonometric Functions')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)
plt.legend()

# Add markers at key points (multiples of π/2)
plt.xticks([0, np.pi/2, np.pi, 3*np.pi/2, 2*np.pi],
           ['0', 'π/2', 'π', '3π/2', '2π'])
plt.show()
```

### Modifying Trigonometric Functions

Let's explore amplitude, frequency, and phase shifts:
- **Amplitude**: A·sin(x) - controls height
- **Frequency**: sin(B·x) - controls how many waves
- **Phase shift**: sin(x + C) - shifts left/right

```python
# Comparing different amplitudes and frequencies
x = np.linspace(0, 4*np.pi, 400)

y1 = np.sin(x)          # Standard sine
y2 = 2 * np.sin(x)      # Double amplitude
y3 = np.sin(2*x)        # Double frequency
y4 = np.sin(x + np.pi/4)  # Phase shift

plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.plot(x, y1, 'b-', linewidth=2)
plt.title('y = sin(x)')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)

plt.subplot(2, 2, 2)
plt.plot(x, y2, 'r-', linewidth=2)
plt.title('y = 2·sin(x) - Amplitude = 2')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)

plt.subplot(2, 2, 3)
plt.plot(x, y3, 'g-', linewidth=2)
plt.title('y = sin(2x) - Frequency doubled')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)

plt.subplot(2, 2, 4)
plt.plot(x, y4, 'purple', linewidth=2)
plt.title('y = sin(x + π/4) - Phase shift')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)

plt.tight_layout()
plt.show()
```

### Exercise 3: Trigonometric Functions

Create a plot showing:
1. y = 3·sin(x) with amplitude 3
2. y = sin(3x) with three waves in the same space

Plot them on the same graph to compare!

```python
# Your code here
x = np.linspace(0, 2*np.pi, 400)

# Calculate your y-values


# Create your plot
```

---

## Part 4: Parametric Equations - Circles and Ellipses

For some shapes, we define both x and y as functions of a parameter (usually t).

**For a circle:**
- x = r·cos(t)
- y = r·sin(t)

where r is the radius and t goes from 0 to 2π

### Plot a Circle with Radius 5

```python
t = np.linspace(0, 2*np.pi, 200)
r = 5

x = r * np.cos(t)
y = r * np.sin(t)

plt.figure(figsize=(8, 8))
plt.plot(x, y, 'b-', linewidth=2, label='Circle: r = 5')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parametric Plot: Circle')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)
plt.axvline(x=0, color='k', linewidth=0.5)
plt.axis('equal')  # Makes the circle look circular (not stretched)
plt.legend()
plt.show()
```

### Ellipses

An ellipse is like a stretched circle:
- x = a·cos(t)
- y = b·sin(t)

where a and b are the semi-major and semi-minor axes

```python
# Plot an ellipse
t = np.linspace(0, 2*np.pi, 200)
a = 8  # semi-major axis
b = 4  # semi-minor axis

x = a * np.cos(t)
y = b * np.sin(t)

plt.figure(figsize=(10, 6))
plt.plot(x, y, 'r-', linewidth=2, label=f'Ellipse: a={a}, b={b}')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Parametric Plot: Ellipse')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)
plt.axvline(x=0, color='k', linewidth=0.5)
plt.axis('equal')
plt.legend()
plt.show()
```

### Exercise 4: Parametric Plots

1. Plot a circle with radius 3
2. On the same graph, plot an ellipse with a=6 and b=2

Use different colors to distinguish them!

```python
# Your code here
t = np.linspace(0, 2*np.pi, 200)

# Circle


# Ellipse


# Create your plot
```

---

## Part 5: Complex Functions and Combinations

Let's explore more interesting mathematical functions by combining what we've learned.

### Damped Oscillation

This describes how oscillations decay over time - common in physics!

```python
# y = e^(-x/10) * sin(x)
x = np.linspace(0, 20, 400)
y = np.exp(-x/10) * np.sin(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y, 'b-', linewidth=2, label='y = e^(-x/10)·sin(x)')
# Also plot the envelope (decay function)
plt.plot(x, np.exp(-x/10), 'r--', linewidth=1, alpha=0.7, label='Envelope: e^(-x/10)')
plt.plot(x, -np.exp(-x/10), 'r--', linewidth=1, alpha=0.7)

plt.xlabel('x')
plt.ylabel('y')
plt.title('Damped Oscillation')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)
plt.legend()
plt.show()
```

### Gaussian (Normal) Distribution

The famous bell curve from statistics!

```python
# y = e^(-x²/2)
x = np.linspace(-5, 5, 400)
y = np.exp(-x**2 / 2)

plt.figure(figsize=(10, 6))
plt.plot(x, y, 'purple', linewidth=2, label='y = e^(-x²/2)')
plt.fill_between(x, y, alpha=0.3)  # Fill under the curve

plt.xlabel('x')
plt.ylabel('y')
plt.title('Gaussian (Bell) Curve')
plt.grid(True, alpha=0.3)
plt.axhline(y=0, color='k', linewidth=0.5)
plt.axvline(x=0, color='k', linewidth=0.5)
plt.legend()
plt.show()
```

---

## Part 6: Bonus - Polar Coordinates

Polar coordinates use radius (r) and angle (θ) instead of x and y. Perfect for spiral patterns and flowers!

### Archimedean Spiral

```python
# r = θ
theta = np.linspace(0, 4*np.pi, 400)
r = theta

# Create polar plot
plt.figure(figsize=(8, 8))
ax = plt.subplot(111, projection='polar')
ax.plot(theta, r, 'b-', linewidth=2)
ax.set_title('Archimedean Spiral: r = θ', pad=20)
plt.show()
```

### Rose Curves

Creates beautiful flower patterns!

```python
# r = cos(n*θ)
theta = np.linspace(0, 2*np.pi, 1000)

fig, axes = plt.subplots(2, 2, figsize=(12, 12), subplot_kw=dict(projection='polar'))

# Different values of n create different numbers of petals
for idx, n in enumerate([2, 3, 4, 5]):
    ax = axes[idx//2, idx%2]
    r = np.cos(n * theta)
    ax.plot(theta, r, linewidth=2)
    ax.set_title(f'Rose curve: r = cos({n}θ)', pad=20)
    ax.grid(True)

plt.tight_layout()
plt.show()
```

---

## Final Challenge: Create Your Own Function

Combine different mathematical operations to create an interesting function. Here are some ideas:

1. Combine sine waves: `y = sin(x) + 0.5·sin(3x)`
2. Polynomial + trig: `y = x² + sin(5x)`
3. Product of functions: `y = x·sin(x)`
4. Your own creation!

Make it visually interesting and explain what you created.

```python
# Your final project here!
x = np.linspace(-10, 10, 500)

# Create your own function
y = # YOUR CREATIVE EQUATION HERE

# Make a beautiful plot
plt.figure(figsize=(12, 8))

# Add your plotting code

plt.show()
```

---

## Summary: Key Takeaways

1. **The Process**: Always create x-values first (using `np.linspace()`), then calculate y-values from your equation

2. **Basic Structure**:
   ```python
   x = np.linspace(start, stop, num_points)
   y = # your equation using x
   plt.plot(x, y)
   ```

3. **Make it Clear**: Always add labels, titles, grids, and legends to your plots

4. **Experiment**: Change parameters to see how functions behave - this builds intuition!

5. **Parametric Equations**: For circles, ellipses, and complex shapes, define both x and y as functions of a parameter t

---

## Common Plotting Parameters

### Line Styles
- `'-'` solid line
- `'--'` dashed line
- `':'` dotted line
- `'-.'` dash-dot line

### Colors
- `'b'` blue
- `'r'` red
- `'g'` green
- `'k'` black
- `'purple'`, `'orange'`, etc.

### Markers
- `'o'` circles
- `'s'` squares
- `'^'` triangles
- `'*'` stars

### Example
```python
plt.plot(x, y, 'r--', linewidth=2, marker='o', markersize=5)
```

---

## Next Steps

- Explore 3D plotting with `mpl_toolkits.mplot3d`
- Learn about contour plots for multivariable functions
- Study animation with matplotlib to show how functions evolve
- Practice with real-world data and curve fitting

---

## Troubleshooting Tips

**Import errors**: Make sure you're using the correct Jupyter kernel that has numpy and matplotlib installed

**Plots not showing**: Include `%matplotlib inline` at the top of your notebook

**Stretched circles**: Use `plt.axis('equal')` to maintain aspect ratio

**Need more points**: Increase the third argument in `np.linspace()` for smoother curves

---

## Resources

- Matplotlib documentation: https://matplotlib.org/
- NumPy documentation: https://numpy.org/
- Python plotting gallery: https://matplotlib.org/stable/gallery/

Happy plotting!
