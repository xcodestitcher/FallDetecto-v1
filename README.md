# FallDetecto-v1

**FallDetecto** is a Python and ONNX-based computer vision project designed to detect fall incidents from images using a custom-trained YOLOv8 model exported in ONNX format.
It includes a lightweight web interface that allows users to upload images and get instant detection results directly in the browser.

---

## 📦 Dataset

The dataset consists of images of people falling in various conditions and bounding boxes as their labels.

The dataset is a combination of publicly available datasets at Roboflow (https://universe.roboflow.com/roboflow-universe-projects/fall-detection-ca3o8), contains 10.973 JPG images (640x640px), enhanced with augmentation to improve generalization.

### 🔄 Data Augmentation

To improve model generalization, each original image is augmented with these techniques:

- Flip: Horizontal
- Crop: 0% Minimum Zoom, 20% Maximum Zoom
- Rotation: Between -12° and +12°
- Shear: ±2° Horizontal, ±2° Vertical
- Grayscale: Apply to 10% of images
- Hue: Between -20° and +20°
- Saturation: Between -20% and +20%
- Brightness: Between -20% and +20%
- Exposure: Between -20% and +20%
- Blur: Up to 0.75px
- Cutout: 5 boxes with 3% size each

---

## ⚙️ Features

- 🔍 Detect fall incidents from uploaded images
- 🧠 Inference using YOLOv8 in ONNX format
- 🌐 Lightweight web interface built with HTML + JS + onnxruntime-web
- 🚀 Easy deployment via Google Colab + Ngrok
- 🖼️ Displays uploaded image along with detection results
- 🎯 Adjustable confidence threshold to reduce false positives

---

## 🧪 Model Performance

Based on the Precision-Recall Curve, the model achieved:
- mAP@0.5 = 0.792
- High precision at low recall, making it suitable for applications where accurate fall detection is a priority
- Recommended confidence threshold: between 0.5 and 0.6

---

## 🚀 How to Run

The project can be deployed and accessed via browser using Google Colab.

### 🧠 Run on Colab with Ngrok (Web Deployment)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/FallDetecto.git
   cd FallDetecto

2. **Open falldetecto_web.ipynb in Google Colab**
   The notebook handles model loading, web server setup, and ngrok tunneling.

3. **Insert your Ngrok API Key**
   ```bash
   from pyngrok import ngrok
   ngrok.set_auth_token("YOUR_NGROK_API_KEY")

4. **Upload your YOLOv8 ONNX model file**
    Example: best.onnx

5. **Access the web app**
    After running all cells, you'll get a public URL such as:
    ```bash
    🌐 Web App URL: https://abc123.ngrok.io

---

## 🙋‍♂️ Author
Developed as part of a Computer Vision project at **Politeknik Caltex Riau**.

---

## 📁 Folder Structure
   ```bash
   FallDetecto-v1/
    │
    ├── FallDetection-Models/
    │   └── yolo-fall-v1/
    │       ├── weights/
    │       │   ├── best.pt                 # Best YOLOv8 model (PyTorch)
    │       │   ├── best.onnx               # Exported model in ONNX format
    │       │   └── last.pt                 # Last checkpoint
    │       │
    │       ├── F1_curve.png                # F1 score vs confidence threshold
    │       ├── PR_curve.png                # Precision-Recall curve
    │       ├── P_curve.png                 # Precision curve
    │       ├── R_curve.png                 # Recall curve
    │       ├── confusion_matrix.png        # Confusion matrix
    │       ├── confusion_matrix_normalized.png
    │       ├── labels.jpg                  # Class labels visualization
    │       ├── labels_correlogram.jpg      # Correlation between predicted labels
    │       ├── args.yaml                   # Training configuration
    │       ├── results.csv                 # Training result metrics
    │       └── results.png                 # Training result plots
    │
    └── README.md