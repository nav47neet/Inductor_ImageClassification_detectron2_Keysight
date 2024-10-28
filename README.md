# Inductor_ImageClassification_detectron2_Keysight

This project utilizes the Detectron2 library from Facebook AI Research for object detection tasks. The notebook includes steps for setting up the environment, loading data, training a model, and evaluating its performance.

## Installation

To ensure all dependencies are met, follow these steps:

1. **Clone the repository**:
```bash
git clone https://github.com/nav47neet/Inductor_ImageClassification_detectron2_Keysight.git
```

2. **Install Dependencies**:
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install 'git+https://github.com/facebookresearch/detectron2.git'
pip install labelme jsonmerg
```

## Project Structure

```
Inductor_ImageClassification_detectron2_Keysight/
├── Keysight_assignment2.ipynb          # Main notebook file
├── train/                              # Training data directory
└── README.md                           # Project documentation
```

## Key Components

### 1. Dataset

We manually annotated the component coordinates using labelme since they couldn't be extracted directly from KiCad software. This generated a dataset suitable for training.

<div align="center">
  <img src="https://github.com/user-attachments/assets/ada1ed50-ead4-4cfa-a3ec-ae5d4cf22b1f" width="300" height="300" alt="Annotation Example 1">
  <img src="https://github.com/user-attachments/assets/64e6ce93-f5a1-4321-9360-5b3a3eeafd1e" width="300" height="300" alt="Annotation Example 2">
</div>

These annotations were used to generate coordinates in JSON format, which along with the images, were used to train our model.

To help the model differentiate between inductors and similar shapes, we also included annotated doughnut images in the training set:

<div align="center">
  <img src="https://github.com/user-attachments/assets/a6bdb070-5dac-43ea-80e7-330c9430ab1d" width="300" height="300" alt="Doughnut Example 1">
  <img src="https://github.com/user-attachments/assets/95883884-0287-4b01-87b7-7934db481c33" width="300" height="300" alt="Doughnut Example 2">
</div>

### 2. Model

#### Faster R-CNN Model

Faster R-CNN is a state-of-the-art object detection framework combining a Region Proposal Network (RPN) with a Fast R-CNN detector, allowing efficient and accurate object detection.

#### Key Features:

- **Two-Stage Detection**: 
  - First stage: RPN generates region proposals
  - Second stage: Detection network classifies and refines these proposals

- **Backbone Network**: 
  - Utilizes ResNet with Feature Pyramid Networks (FPN)
  - Enables robust feature extraction at multiple scales

- **Pre-trained Weights**: 
  - Trained on the COCO dataset
  - Provides strong initialization for custom tasks

#### Applications:

Faster R-CNN is widely used in various fields, including:
- Autonomous driving
- Video surveillance
- Robotics

This makes it ideal for detecting objects like **Inductor** and **Donut** in this project.

## Output

The trained model successfully identifies inductors from given test images.

<div align="center">
  <img src="https://github.com/user-attachments/assets/3e9fdf6a-4bc2-4291-80f4-10ec5614d76b" alt="Model Output Example" width="600">
</div>

### Using the Trained Model on Custom Test Images

1. **Download the Model**:
   - Get `model_final.pth` from [Google Drive](https://drive.google.com/drive/folders/1V2PTOiJeVD8cVqoWO1v7rZVl7acQBrhR?usp=sharing)

2. **Run Inference**:
```python
from detectron2.engine import DefaultPredictor
from detectron2.utils.visualizer import Visualizer
import cv2
from google.colab.patches import cv2_imshow

# Configure the model
cfg.MODEL.WEIGHTS = "../model_final.pth"         //use model path
cfg.MODEL.ROI_HEADS.SCORE_THRESH_TEST = 0.8
cfg.MODEL.DEVICE = "cuda"

# Initialize predictor
predictor = DefaultPredictor(cfg)

# Load and process image
img = cv2.imread("../test.png")                  //use test image path
outputs = predictor(img)

# Visualize results
v = Visualizer(img[:, :, ::-1], metadata=metadata, scale=0.8)
out = v.draw_instance_predictions(outputs["instances"].to("cpu"))

# Display results
cv2_imshow(out.get_image()[:, :, ::-1])
cv2.waitKey(0)
cv2.destroyAllWindows()
```


### Group Members:
1. **Navneet Mishra (MT23049)**
2. **Monika Singh (2021169)**
