# Sudoku Solver Using OpenCV and Python

This project combines computer vision and deep learning to create a fully automated Sudoku solver. It can detect a Sudoku board from a photo, recognize the given digits, solve the puzzle with a backtracking algorithm, and superimpose the solution back onto the original image.

---

## Features

- **Automatic Sudoku board detection** from photos
- **Perspective correction** for accurate extraction
- **Digit recognition** using a pre-trained deep learning OCR model
- **Sudoku solving** via a backtracking algorithm
- **Solution overlay** on the original Sudoku image
- Handles both printed and (optionally) handwritten puzzles

---

## Project Structure

.
├── sudoku_solver.py # Main script
├── model-OCR.h5 # Trained OCR model for digit recognition
├── utils.py # Helper functions for processing and solving
├── requirements.txt # Project dependencies
├── sample_images/ # Example Sudoku images
└── README.md


---

## Requirements

- Python 3.x
- OpenCV
- TensorFlow / Keras
- numpy
- imutils

Install all dependencies using:

pip install -r requirements.txt

---

## How It Works

1. **Board Detection**
   - Converts the input image to grayscale and applies denoising.
   - Detects edges (Canny) and finds the largest contour (assumed Sudoku board).
   - Applies perspective transform for a top-down view.

2. **Cell Extraction**
   - Splits the board image into 81 (9×9) cell images.

3. **Digit Recognition**
   - Each cell is passed through a pre-trained OCR model (`model-OCR.h5`).
   - Outputs a 9×9 number grid (`0` for empty cells).

4. **Sudoku Solving**
   - Applies a backtracking algorithm to fill empty cells.

5. **Solution Overlay**
   - Writes the solved digits onto the original image at correct cell locations.

---

## Usage

python sudoku_solver.py --image path/to/sudoku.jpg

The solution will be saved (e.g., as `solution.jpg`) and/or displayed, depending on script options.

---

## Model Training

- The OCR model is trained on datasets of 28×28 grayscale images of digits (0–9), from sources such as MNIST or custom-augmented printed Sudoku digits.
- You can re-train or fine-tune using similar digit datasets for best results.

---

## Example

**Input:**  
A photo of an unsolved Sudoku puzzle.

**Output:**  
The same photo with the solution digits superimposed in the empty cells.

---

## Notes

- For best accuracy, use clear photos with a direct top-down angle.
- Retraining may be needed for different fonts or handwritten digits.
- You may adapt the OCR model path or cell extraction logic if your Sudoku grid style differs.

---

## References

- OpenCV documentation
- TensorFlow/Keras documentation
- Related tutorials and datasets from DataFlair, Kaggle, and academic resources

---

## License

MIT License


