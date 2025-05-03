# SynthPark: Synthetic Data for Truck Parking Occupancy Prediction

<p align="center">
  <img src="https://via.placeholder.com/600x200.png?text=SynthPark+Banner" alt="SynthPark" />
</p>

<p align="center">
  <a href="https://github.com/eee-Andrew/SynthPark/releases"><img src="https://img.shields.io/github/v/release/yourusername/SynthPark?color=brightgreen" alt="Release"></a>
  <a href="https://github.com/eee-Andrew/SynthPark/blob/main/LICENSE"><img src="https://img.shields.io/github/license/yourusername/SynthPark?color=blue" alt="License"></a>
  <a href="https://github.com/eee-Andrew/SynthPark/issues"><img src="https://img.shields.io/github/issues/yourusername/SynthPark?color=orange" alt="Issues"></a>
</p>

## Overview
**SynthPark** leverages synthetic data generated in Unity 3D to address the scarcity of real-world aerial datasets for truck parking occupancy prediction in autonomous logistics. A YOLOv11-based object detection model is trained on this dataset, achieving robust performance in identifying trucks and parking spots under diverse conditions.

## Features
- **Synthetic Dataset**: A realistic 250m x 90m parking lot environment with dynamic lighting, occlusions, and varied camera angles.
- **Data Augmentation**: Includes geometric transformations, photometric adjustments, and weather effects, producing 250 diverse images.
- **YOLOv11 Model**: Fine-tuned for truck and parking spot detection with mAP50-95 of 0.761 and 3.74ms inference speed.
- **Occupancy Detection**: Uses Non-Maximum Suppression (NMS) for 74% accuracy and 69% F1 score in classifying parking spots.
- **Scalable Solution**: Bypasses legal/ethical constraints of real-world UAV data collection.

## Dataset Details
- **Environment**: Digital twin of a Serbian parking lot (Lat: 45.0466667, Long: 19.2255555) with trucks, roads, and occluding elements.
- **Image Capture**: High-resolution images from 10-50m altitudes, simulating UAV viewpoints.
- **Annotations**: Multi-class labels (`truck`, `parking spot`) for occupancy detection.
- **Augmentation**: Flips, shifts, rotations, brightness/contrast adjustments, noise, weather effects, and CLAHE.

## Model Performance
| Metric            | Value  |
|-------------------|--------|
| mAP50-95          | 0.761  |
| mAP50             | 0.942  |
| Precision         | 0.935  |
| Recall            | 0.877  |
| F1 Score          | 0.69   |
| Inference Speed   | 3.74ms |
| GFLOPs            | 28.6   |
| Parameters        | 11.1M  |

Training used an NVIDIA RTX 3060 GPU, batch size of 16, and up to 500 epochs with early stopping.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/SynthPark.git
   cd SynthPark
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Download pretrained YOLOv11 weights from [Ultralytics](https://docs.ultralytics.com/models/yolov11/) or Roboflow (PKLot dataset).
4. Install Unity 3D (HDRP-compatible version) for dataset generation.

## Usage
### 1. Generate Synthetic Dataset
- Configure the Unity environment (see `unity_assets/`).
- Run dataset generation scripts:
  ```bash
  python scripts/generate_dataset.py
  ```

### 2. Train the Model
```bash
python scripts/train_yolov11.py --data dataset.yaml --weights yolov11.pt --epochs 500 --batch-size 16
```

### 3. Evaluate Performance
```bash
python scripts/evaluate.py --model yolov11_trained.pt --test-data test_images/
```

### 4. Run Inference
```bash
python scripts/detect.py --model yolov11_trained.pt --source new_images/
```

## Directory Structure
```
SynthPark/
├── dataset/
│   ├── images/               # Synthetic images
│   ├── labels/               # Annotations
│   └── dataset.yaml          # Dataset config
├── scripts/
│   ├── generate_dataset.py   # Dataset generation
│   ├── train_yolov11.py      # Training
│   ├── evaluate.py           # Evaluation
│   ├── detect.py             # Inference
├── unity_assets/             # Unity environment
├── requirements.txt          # Dependencies
└── README.md                 # Documentation
```

## Future Work
- Real-world deployment on physical drones.
- Expand dataset with more scenarios.
- Optimize model for edge devices.

## Acknowledgments
Funded by:
- European Union Agency for the Space Programme (EUSPA), Grant No. 101129658.
- Project TAEDR-0535864, National Recovery and Resilience Plan Greece 2.0 (NextGenerationEU).

## Citation
```bibtex
@article{valvis2025synthpark,
  title={SynthPark: Leveraging Synthetic Data for Occupancy Prediction in Autonomous Logistics},
  author={Valvis, Andreas and Balaska, Vasiliki and Kansizoglou, Ioannis and Bampis, Loukas and Gasteratos, Antonios},
  journal={TBD},
  year={2025}
}
```

## License
[MIT License](LICENSE)

## Contact
- Andreas Valvis: [avalvis@pme.duth.gr](mailto:avalvis@pme.duth.gr)
- Vasiliki Balaska: [vbalaska@pme.duth.gr](mailto:vbalaska@pme.duth.gr)

---

⭐ **Star this repo** if you find it useful!  
🐛 Report issues or contribute at [GitHub Issues](https://github.com/yourusername/SynthPark/issues).
