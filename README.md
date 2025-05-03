# SynthPark
Leveraging Synthetic Data for Occupancy Prediction in Autonomous Logistics
Overview

SynthPark is a project focused on generating and utilizing synthetic data to enhance truck parking occupancy prediction in autonomous logistics. By leveraging a realistic parking lot environment created in Unity 3D, this project addresses the scarcity of real-world aerial datasets for truck detection. The synthetic dataset is used to train a YOLOv11-based object detection model, achieving robust performance in identifying trucks and parking spots under diverse conditions.

Features





Synthetic Dataset Generation: A digital twin of a real-world parking lot (Serbia, Lat: 45.0466667, Long: 19.2255555) is constructed using Unity 3D, incorporating dynamic lighting, varied camera angles, and realistic occlusions.



Data Augmentation: Comprehensive augmentation techniques (e.g., geometric transformations, photometric adjustments, weather effects) to simulate real-world variability, resulting in 250 diverse images.



Object Detection Model: YOLOv11 model fine-tuned on the synthetic dataset, achieving a mean Average Precision (mAP50-95) of 0.761 and inference speed of 3.74ms per image.



Parking Occupancy Detection: Non-Maximum Suppression (NMS) applied to classify parking spots as occupied (Class 1) or unoccupied (Class 0), with 74% accuracy and a 69% F1 score.



Scalable Framework: Overcomes legal and ethical constraints of real-world UAV data collection, offering a cost-effective solution for autonomous logistics.

Dataset Details





Environment: A 250m x 90m parking lot with trucks, roads, trees, streetlights, and other occluding elements, rendered using Unity's High Definition Render Pipeline (HDRP).



Image Capture: High-resolution images from simulated UAV viewpoints (10-50m altitude) with varying occupancy scenarios (fully occupied, semi-occupied, empty).



Annotations: Multi-class labels for 'truck' and 'parking spot' to support occupancy detection.



Augmentation: Techniques include flips, shifts, scaling, rotations, brightness/contrast adjustments, noise, weather effects, and CLAHE for enhanced robustness.

Model Performance

The YOLOv11 model was trained on the synthetic dataset with pretrained weights from the PKLot dataset. Key metrics:





mAP50-95: 0.761



mAP50: 0.942



Precision: 0.935



Recall: 0.877



F1 Score: 69%



Inference Speed: 3.74ms per image



Computational Efficiency: 28.6 GFLOPs, 11.1M parameters

Training was conducted on an NVIDIA RTX 3060 GPU (8GB VRAM) with a batch size of 16 and up to 500 epochs, using early stopping to prevent overfitting.
