# Opening and Closing Operations Using OpenCV

## Aim

To implement morphological Opening and Closing operations on an image using Python and OpenCV.

## Learning Objectives

- Understand morphological image processing.
- Learn the Opening operation.
- Learn the Closing operation.
- Remove small foreground noise using Opening.
- Fill small holes and gaps using Closing.

## Software Used

- Anaconda – Python
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

1. Import the required libraries.
2. Create a binary image using NumPy.
3. Add small foreground noise and holes to the image.
4. Display the original image.
5. Create a structuring element (kernel).
6. Apply the Opening operation using erosion followed by dilation.
7. Apply the Closing operation using dilation followed by erosion.
8. Display and compare the original, opened, and closed images.

## Program

### Step 1: Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 2: Create an Input Binary Image

```python
img = np.zeros((300, 500), dtype=np.uint8)

cv2.rectangle(img, (80, 80), (220, 220), 255, -1)
cv2.circle(img, (350, 150), 70, 255, -1)

# Add small foreground noise
noise_points = [(30, 30), (45, 80), (260, 40),
                (280, 250), (450, 270), (470, 60)]

for x, y in noise_points:
    cv2.circle(img, (x, y), 3, 255, -1)

# Add small holes inside foreground objects
cv2.circle(img, (130, 130), 4, 0, -1)
cv2.circle(img, (180, 180), 4, 0, -1)
cv2.circle(img, (350, 150), 5, 0, -1)

plt.figure(figsize=(8, 5))
plt.imshow(img, cmap="gray")
plt.title("Original Binary Image")
plt.axis("off")
plt.show()
```

### Step 3: Create a Structuring Element (Kernel)

```python
kernel = np.ones((5, 5), np.uint8)

print("Structuring Element:")
print(kernel)
```

### Step 4: Perform Morphological Opening

Opening consists of Erosion followed by Dilation.

```python
opening = cv2.morphologyEx(
    img,
    cv2.MORPH_OPEN,
    kernel,
    iterations=1
)

plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
plt.imshow(img, cmap="gray")
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(opening, cmap="gray")
plt.title("Opening Operation")
plt.axis("off")

plt.show()
```

### Step 5: Perform Morphological Closing

Closing consists of Dilation followed by Erosion.

```python
closing = cv2.morphologyEx(
    img,
    cv2.MORPH_CLOSE,
    kernel,
    iterations=1
)

plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
plt.imshow(img, cmap="gray")
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(closing, cmap="gray")
plt.title("Closing Operation")
plt.axis("off")

plt.show()
```

### Step 6: Compare Opening and Closing Results

```python
images = [
    ("Original Image", img),
    ("Opening", opening),
    ("Closing", closing)
]

plt.figure(figsize=(14, 5))

for i, (title, result) in enumerate(images):
    plt.subplot(1, 3, i + 1)
    plt.imshow(result, cmap="gray")
    plt.title(title)
    plt.axis("off")

plt.tight_layout()
plt.show()
```

## Developed By

- **Name:** Shaajini N
- **Register No:** 212225040395

## Output

### 1. Original Image

- A binary image is created using NumPy.
- Foreground objects are created using OpenCV.
- Small foreground noise and holes are added.
- The original image is displayed.

### 2. Opening Operation

- Opening is performed using a 5 × 5 kernel.
- Erosion is followed by Dilation.
- Small foreground noise is removed.
- Thin protrusions are eliminated.
- Larger foreground objects are preserved.

### 3. Closing Operation

- Closing is performed using a 5 × 5 kernel.
- Dilation is followed by Erosion.
- Small holes and gaps are filled.
- Foreground objects become more continuous.

### 4. Comparison Output

- Original image, opened image, and closed image are displayed together.
- The differences between both morphological operations are observed.

## Applications

### Opening

- Removing small foreground noise.
- Image preprocessing.
- Improving object segmentation.

### Closing

- Filling small holes in objects.
- Connecting nearby components.
- Improving object continuity.

## Advantages

### Opening

- Removes unwanted foreground noise.
- Preserves larger object structures.
- Improves image quality.

### Closing

- Fills small gaps and holes.
- Improves object continuity.
- Enhances segmented regions.

## Result

Thus, the morphological operations Opening and Closing were successfully implemented using Python and OpenCV. Opening removes small foreground noise, whereas Closing fills small holes and gaps in foreground objects.

## Output Screenshots

Add your Jupyter Notebook screenshots below:

- **Output 1:** Original Binary Image
- **Output 2:** Structuring Element
- **Output 3:** Opening Operation
- **Output 4:** Closing Operation
- **Output 5:** Comparison of Original, Opening, and Closing

## Instructions

1. Open Anaconda Navigator and launch Jupyter Notebook.
2. Run each program separately in the given order.
3. Verify the Opening and Closing outputs.
4. Capture screenshots of all outputs.
5. Copy the README content into your GitHub repository.
6. Commit the changes.
7. Attach the lab report PDF separately in LMS.
8. Mention the GitHub repository URL in the submission text.
