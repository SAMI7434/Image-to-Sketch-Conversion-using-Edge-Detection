# Image to Sketch Conversion using Edge Detection

A Python-based Jupyter Notebook project that converts ordinary images into pencil-sketch style artwork using classical computer vision techniques — specifically Gaussian blurring and Canny edge detection.

---

## Overview

This project demonstrates a simple yet effective image processing pipeline that transforms any input photograph into a pencil sketch. The approach leverages OpenCV's image processing utilities to:

1. Load and display the original image.
2. Convert the image to grayscale.
3. Apply Gaussian blur to smooth out noise.
4. Detect edges using the Canny edge detector.
5. Invert the edge map to produce a white-on-black pencil sketch effect.
6. Save the final sketch to disk.

---

## Pipeline

```
Original Image
     │
     ▼
Grayscale Conversion  (cv2.cvtColor → COLOR_BGR2GRAY)
     │
     ▼
Gaussian Blur         (cv2.GaussianBlur, kernel 5×5)
     │
     ▼
Canny Edge Detection  (cv2.Canny, thresholds 60 / 100)
     │
     ▼
Bitwise Inversion     (cv2.bitwise_not)
     │
     ▼
Pencil Sketch Output  (saved as sketch.jpg)
```

---

## Requirements

| Package | Purpose |
|---------|---------|
| Python 3.x | Runtime |
| OpenCV (`cv2`) | Image loading, processing, and saving |
| Matplotlib | Displaying images inside the notebook |
| Jupyter Notebook | Interactive development environment |

Install dependencies with pip:

```bash
pip install opencv-python matplotlib notebook
```

---

## Usage

1. **Clone the repository**

   ```bash
   git clone https://github.com/SAMI7434/Image-to-Sketch-Conversion-using-Edge-Detection.git
   cd Image-to-Sketch-Conversion-using-Edge-Detection
   ```

2. **Install dependencies**

   ```bash
   pip install opencv-python matplotlib notebook
   ```

3. **Open the notebook**

   ```bash
   jupyter notebook Untitled1-checkpoint.ipynb
   ```

4. **Update the image paths**

   In the notebook's second cell, replace the hardcoded file paths with the paths to your own images:

   ```python
   img  = cv2.imread("path/to/your/image1.png")
   img1 = cv2.imread("path/to/your/image2.jpg")
   ```

5. **Run all cells** (`Kernel → Restart & Run All`)

   The notebook will display each intermediate stage and save the final sketches as `sketch1.jpg` and `sketch2.jpg` in the project directory.

---

## Output

The notebook generates and displays the following stages side by side:

| Stage | Description |
|-------|-------------|
| Original Image | The raw input photograph |
| Grayscale Image | Single-channel luminance representation |
| Blurred Image | Noise-reduced version using Gaussian filter |
| Edge Detected Image | Raw Canny edges (black on white) |
| Pencil Sketch | Inverted edges — final sketch result |

---

## How It Works

### 1. Grayscale Conversion
Color information is not needed for edge detection. Converting to grayscale reduces the image to a single intensity channel, simplifying subsequent processing.

### 2. Gaussian Blur
A 5×5 Gaussian kernel smooths the image, reducing high-frequency noise that would otherwise create spurious edges.

### 3. Canny Edge Detection
The Canny algorithm finds edges by:
- Computing intensity gradients.
- Applying non-maximum suppression to thin edges.
- Using two thresholds (60 and 100) for hysteresis edge tracking.

### 4. Bitwise Inversion
The Canny output is a black background with white edges. Inverting it produces a white background with dark edges — visually resembling a pencil sketch on paper.

---

## Example

```
Input:  A photograph of a person or scene
Output: sketch1.jpg / sketch2.jpg — a pencil-sketch rendering of the input
```

---

## Project Structure

```
Image-to-Sketch-Conversion-using-Edge-Detection/
├── Untitled1-checkpoint.ipynb   # Main Jupyter Notebook
├── sketch1.jpg                  # Output sketch (generated on run)
├── sketch2.jpg                  # Output sketch (generated on run)
└── README.md                    # Project documentation
```

---

## License

This project is open source and available for educational and personal use.
