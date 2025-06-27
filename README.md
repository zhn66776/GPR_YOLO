# GPR Hyperbola Detection using YOLOv5
This project leverages YOLOv5 to detect hyperbolas in Ground Penetrating Radar (GPR) images — a key step in identifying buried objects like pipelines, utilities, or archaeological remains.

## Project Structure
1. The dataset includes 171 GPR scans from-  https://github.com/irenexychen/gpr-data-classifier/tree/master/hyperbola-classifier/images. Theimages are divided in two categories- grey scale images and blue tinted images.
2. These images were augmented to increase model performance during training, resulting in 3096 images total
3. The transformed images are trained on yolov5 model using pre trained coco weights

## Objective

Detect hyperbolic signatures in GPR images using object detection. These hyperbolas usually indicate subsurface objects, and automating their detection saves time and reduces manual inspection errors.

## Model Used

- **YOLOv5s** (pre-trained on COCO)
- Trained for **50 epochs**
- Optimizer: **SGD** with momentum 0.937
- Batch size: **8**
- Input size: **256×256**

## Results

| Metric         | Value   |
|----------------|---------|
| Precision      | 0.366   |
| Recall         | 0.263   |
| mAP@0.5        | 0.210   |
| mAP@0.5:0.95   | 0.087   |

YOLOv5 achieved moderate accuracy, suggesting improvement potential through augmentation, more data, or YOLOv7.

## Visualizations

- `results.png`: Training and validation loss/mAP curves
- `runs/detect/`: Inference results on test images
- Visual comparison of predictions and ground truth available in notebooks

## How to Run

1. Upload the dataset in the correct format
2. Run training:

```bash
python train.py --img 256 --batch 8 --epochs 50 \
--data gpr_data.yaml --weights yolov5s.pt --project runs/train_gpr \
--name yolov5s_gpr --exist-ok
python detect.py --weights best.pt --source images/validation --img 256

## Future Work
Integrate YOLOv7 for better performance

Improve annotations

Apply domain adaptation for different GPR devices

