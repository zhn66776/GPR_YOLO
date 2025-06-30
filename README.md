# 🛰️ GPR Hyperbola Detection using YOLOv5

This project applies **YOLOv5** to detect hyperbolas in Ground Penetrating Radar (GPR) images — a critical step for identifying buried objects such as pipelines, utilities, and archaeological features. Automating hyperbola detection enhances survey accuracy and reduces manual effort in subsurface interpretation.

## 📁 Dataset Overview

- **Source**: [GPR Dataset by irenexychen](https://github.com/irenexychen/gpr-data-classifier/tree/master/hyperbola-classifier/images)
- **Original Images**: 171 scans (grayscale and blue-tinted)
- **Augmented Set**: Expanded to 3096 images via transformations (flipping, noise addition, contrast adjustment, cropping)
- **Annotation Format**: YOLO (bounding boxes around hyperbolas)
- **Folder Structure**:
  
YOLO-Dataset/
├── images/
│ ├── training/
│ └── validation/
├── labels/
│ ├── training/
│ └── validation/
└── gpr_data.yaml
---

## 🎯 Objective

To automate the detection of hyperbolic reflections — commonly associated with subsurface targets — using a fast and lightweight object detection model, reducing reliance on manual inspection in GPR imagery analysis.

## 🧠 Model Details

- **Model**: YOLOv5s (pretrained on COCO)
- **Epochs**: 50
- **Batch Size**: 8
- **Image Size**: 256×256
- **Optimizer**: SGD
- **Momentum**: 0.937
- **Weight Decay**: 0.0005

---

## 📊 Training & Evaluation Metrics

| Metric                | Value   |
|------------------------|---------|
| Precision              | 0.366   |
| Recall                 | 0.263   |
| mAP@0.5                | 0.210   |
| mAP@0.5:0.95           | 0.087   |
| Final Training Loss    | (Logged in `results.csv`) |
| Final Validation Loss  | (Logged in `results.csv`) |

> 💡 The results indicate modest performance. Detection quality can be enhanced by increasing dataset diversity, improving label quality, or training with larger models like YOLOv7 or YOLOv8.

## 📈 Visualizations

- **Training Curves**: `runs/train_gpr/yolov5s_gpr/results.png`
- **Predicted Outputs**: `runs/detect/yolov5_infer/`
- **Side-by-side Visuals**: Included via matplotlib to compare ground truth vs predicted bounding boxes.

  ![image](https://github.com/user-attachments/assets/7d6b05a2-3f06-4869-8b37-44d0c3300e26)

  ![image](https://github.com/user-attachments/assets/71a5a73c-bf5a-470f-beab-e348db365c90)


## 🛠️ How to Run

### 1. Clone YOLOv5 Repository
```bash
git clone https://github.com/ultralytics/yolov5
cd yolov5
pip install -r requirements.txt

**### 2. Train the Model**
bash
Copy
Edit
python train.py \
  --img 256 \
  --batch 8 \
  --epochs 50 \
  --data /path/to/gpr_data.yaml \
  --weights yolov5s.pt \
  --project runs/train_gpr \
  --name yolov5s_gpr \
  --exist-ok

**3. Run Inference**
bash
Copy
Edit
python detect.py \
  --weights runs/train_gpr/yolov5s_gpr/weights/best.pt \
  --img 256 \
  --conf 0.3 \
  --source /path/to/images/validation \
  --name yolov5_infer \
  --save-txt \
  --exist-ok

****Future Work
✅ Upgrade to YOLOv7/YOLOv8 for better accuracy and mAP

✅ Expand dataset with real-world noisy GPR samples

✅ Apply domain adaptation techniques across GPR devices

✅ Explore semi-supervised learning to reduce annotation effort

**Acknowledgments**
Dataset: irenexychen/gpr-data-classifier
Framework: Ultralytics YOLOv5
Environment: Google Colab, Python 3.11, CUDA (Tesla T4)
