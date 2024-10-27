# Inductor_ImageClassification_detectron2_Keysight



This project utilizes the Detectron2 library from Facebook AI Research for object detection tasks. The notebook includes steps for setting up the environment, loading data, training a model, and evaluating its performance.

## Table of Contents

- [Installation](#installation)
- [Setup](#setup)
- [Project Structure](#project-structure)
- [Key Components](#key-components)
- [Results](#results)
- [License](#license)

## Installation

To ensure all dependencies are met, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/nav47neet/Inductor_ImageClassification_detectron2_Keysight.git

2. **Installing Dependencies**:
   ```bash
   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
   pip install 'git+https://github.com/facebookresearch/detectron2.git'
   pip install labelme jsonmerg
   ```

3. **Project Structure**:
   ```bash
      Inductor_ImageClassification_detectron2_Keysight/
   ├── Untitled7.ipynb          
   ├── train/                    
   ├── model.pth                 
   └── README.md

4. **DataSet**:
   
   We were unable to extract coordinates of a component from KiCad software so we thus annotated the coordinates using labelme and generated dataset for the training.

   <table style="border: none;">
  <tr>
    <td style="border: none;"><img src="https://github.com/user-attachments/assets/ada1ed50-ead4-4cfa-a3ec-ae5d4cf22b1f" width="300"></td>
    <td style="border: none;"><img src="https://github.com/user-attachments/assets/64e6ce93-f5a1-4321-9360-5b3a3eeafd1e" width="300"></td>
  </tr>
</table>

   We used these annotations to generate the coordiantes of these images in a json file and then used these coordinated and the images to train our model.






