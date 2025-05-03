# SynthPark: Synthetic Data for Truck Parking Occupancy Prediction

<p align="center">
  <img src="https://img.shields.io/badge/status-No%20Releases%20Planned-brightgreen" alt="Status">
  <a href="https://github.com/eee-Andrew/SynthPark/blob/main/LICENSE.md"><img src="https://img.shields.io/github/license/eee-Andrew/SynthPark?color=blue" alt="License"></a>
  <a href="https://github.com/eee-Andrew/SynthPark/issues"><img src="https://img.shields.io/github/issues/eee-Andrew/SynthPark?color=orange" alt="Issues"></a>
</p>


**SynthPark**  harnesses Unity 3D Engine to generate a high-quality synthetic dataset, tackling the scarcity of real-world aerial datasets for truck parking occupancy prediction in autonomous logistics. This dataset, designed with diverse conditions and realistic elements, supports the development of object detection solutions. This project is free and open-source, fostering collaborative innovation and data-driven advancements.

-----------------
The Unity environment is available upon request due to its large file size (see the Contact section).
---------------

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

## Directory Structure
```
SynthPark/
├── dataset/
│   ├── images/               # Synthetic images
│   ├── labels/               # Annotations
├── LICENSE                   # MIT License
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
  author={Valvis Andreas, Vasiliki Balaska,Ioannis Kansizoglou, Loukas Bampis and Antonios Gasteratos},
  conf={ECMR},
  year={2025}
}
```

## License
This project is licensed under the [MIT License](LICENSE), making it free and open for development, modification, and distribution. Feel free to contribute and build upon this work!

## Contact
- Andreas Valvis: [avalvis@pme.duth.gr](mailto:avalvis@pme.duth.gr)
---

⭐ **Star this repo** if you find it useful!  
🐛 Report issues or contribute at [GitHub Issues](https://github.com/johndoe/SynthPark/issues).
