# Image-to-Text Converter OCR Project

A small Python project that extracts text from an image using **Optical Character Recognition (OCR)**. It uses Tesseract OCR through `pytesseract`, OpenCV (`cv2`) to load and process the image, and Matplotlib to display the original image and detected text regions.

## Features

- Loads an image from a file.
- Extracts readable text using Tesseract OCR.
- Displays the original image.
- Detects text regions and draws bounding boxes around them.

## Technologies Used

- **Python**
- **Tesseract OCR** — OCR engine that recognizes text in images.
- **pytesseract** — Python wrapper for Tesseract.
- **OpenCV** — loads and handles images.
- **Matplotlib** — displays images and results.
- **Jupyter Notebook** — runs the project cells interactively.

## Project Files

```text
image-to-text-ocr/
├── OCR.ipynb       # Main notebook
├── image1.png      # Input image (add your own image)
└── README.md       # Project documentation
```

## Requirements

- Windows 10/11, macOS, or Linux
- Python (the notebook was prepared with Python; Python 3.13 may work depending on package compatibility)
- Tesseract OCR installed separately from Python packages
- An image containing text, such as a PNG or JPG

## Setup on Windows 11

### 1. Install Tesseract OCR

1. Install the Windows version of **Tesseract OCR** from a trusted distribution, such as the UB Mannheim Windows installer:  
   https://github.com/UB-Mannheim/tesseract/wiki
2. During installation, note the installation folder. A common location is:

   ```text
   C:\Program Files\Tesseract-OCR
   ```

3. Open a **new** Command Prompt and check that Tesseract is available:

   ```cmd
   tesseract --version
   ```

If Windows says that `tesseract` is not recognized, add the Tesseract installation folder to your Windows **Path** environment variable, then open a new Command Prompt. Alternatively, set the executable path in your notebook before running OCR:

```python
import pytesseract
pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe"
```

Adjust the path if you installed Tesseract somewhere else.

### 2. Create and activate a Python environment (recommended)

In Command Prompt, move to your project folder and run:

```cmd
python -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
```

### 3. Install Python packages

```cmd
python -m pip install opencv-python pytesseract matplotlib notebook
```

If installation fails with Python 3.13, check the package's current compatibility or use a supported Python version in a separate virtual environment.

### 4. Add an input image

Place an image containing text in the project folder and name it `image1.png`, or update the path in the notebook. The notebook currently uses:

```python
image_path = "/content/image1.png"
```

That path is commonly used in Google Colab. For a local Windows run, change it to a local path, for example:

```python
image_path = r"C:\path\to\your\project\image1.png"
```

Replace the example path with the actual location of your image.

### 5. Run the notebook

From the activated environment and project folder, run:

```cmd
jupyter notebook
```

Open `OCR.ipynb` in the browser and run the cells from top to bottom.

## How It Works

1. **Import libraries** — imports OpenCV, `pytesseract`, and Matplotlib.
2. **Load the image** — reads the input image with `cv2.imread()` and converts its color channels from BGR to RGB for display.
3. **Recognize text** — calls `pytesseract.image_to_string()` and prints the extracted text.
4. **Display the original** — shows the image with Matplotlib.
5. **Find text locations** — calls `pytesseract.image_to_data()` to obtain word-level text and position information.
6. **Draw bounding boxes** — draws rectangles around detected text regions and displays the result.

## Troubleshooting

- **`'apt-get' is not recognized`**: `apt-get` is a Linux package manager and does not run in Windows Command Prompt. Install Tesseract using a Windows installer instead.
- **`TesseractNotFoundError`**: Install Tesseract and either add its folder to `Path` or set `pytesseract.pytesseract.tesseract_cmd` as shown above.
- **Image not found / `cv2.imread()` returns `None`**: Check the image path, spelling, and file extension. Use a raw Windows path such as `r"C:\folder\image1.png"`.
- **No or inaccurate text**: Use a sharper, well-lit image with readable text. Cropping, increasing resolution, or converting to grayscale may improve results.
- **Notebook uses `/content/`**: This is a Colab-style path. Replace it with your actual Windows image path when running locally.

## Limitations

- OCR accuracy depends on image quality, font, orientation, and language.
- Handwriting and complex page layouts may not be recognized accurately.
- The notebook expects an input image at the configured path.
- Tesseract must be installed separately; installing `pytesseract` alone is not enough.

## Example Output

The notebook prints the text recognized from the input image and displays:

- the original image;
- the image with bounding boxes around detected text.

## License

Add a license if you plan to publish or distribute this project. No license is specified in the notebook.
