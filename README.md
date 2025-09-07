This repository contains the implementation, training configuration, and pretrained weights for 
**YOLOv11-based defect detection on interferometric fringe images**, as proposed in our paper:

> *An Integrated Deep Learning Framework for Interferometric Fringe Analysis, combining ResU-Net for phase retrieval and YOLOv11 for defect detection.*  
## 📌 Features
- Based on **Ultralytics YOLOv11 (`ultralytics==8.3.30`)**
- **Backbone:** C3k2  
- **Neck:** HS-FPN with C2PSA attention modules  
- **Head:** Decoupled detection head (classification/regression separated) with C3k2/CBS blocks  
- **Lightweight:** GSConv for efficient computation  
- **Training:** Dynamic label assignment (Dyna-Label)  
- **Augmentation:** Tailored to fringe patterns (mosaic, mixup, speckle noise, local illumination jitter)

---

## 🔧 Installation

Clone this repository and install dependencies:

```bash
git clone https://github.com/Ceciliavair/YOLOv11-Fringe-Defect-Detection.git
cd YOLOv11-Fringe-Defect-Detection

pip install -r requirements.txt

# Install dependencies
pip install -r requirements.txt
Dependencies include:
ultralytics==8.3.30
torch==2.2.0
cuda==12.1
numpy, opencv-python, matplotlib

📂 Project Structure
YOLOv11-Fringe-Defect-Detection/
│
├── README.md
├── requirements.txt
├── yolo.py                  # Training script
├── train_yolov11_fringe.yaml # Training config
├── data/
│   └── data.yaml            # Dataset path definitions
├── weights/
│   └── best.pt              # Trained model weights (or provide download link)
├── logs/
│   └── train.log            # Training log
└── LICENSE

🚀 Training
yolo train cfg=train_yolov11_fringe.yaml
Key training settings:
Image size: 640
Batch size: 16
Epochs: 100
Optimizer: SGD (lr0=0.01, momentum=0.937, weight_decay=0.0005)
Scheduler: Cosine LR
Random seed: 42
🔍 Inference
yolo predict model=weights/best.pt source="data/data.yaml/test/
Results (bounding boxes, confidence scores) will be saved in runs/predict/.

📊 Results
Example detection performance (on synthetic fringe dataset):
<img width="251" height="125" alt="image" src="https://github.com/user-attachments/assets/fd8967df-7d42-4005-a816-cef5e36e47be" />
📜 License
This project is released under the MIT License
📚 Citation
If you use this work, please cite:
@inproceedings{Song2025YOLOFringe,
  title={An Integrated Deep Learning Framework for Interferometric Fringe Analysis},
  author={Song, Yuxin and Others},
  booktitle={Proceedings of [Conference Name]},
  year={2025}
}
