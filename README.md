# Inductor_ImageClassification_detectron2_Keysight



This project utilizes the Detectron2 library from Facebook AI Research for object detection tasks. The notebook includes steps for setting up the environment, loading data, training a model, and evaluating its performance.



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
   
   We could not extract the coordinates of a component from KiCad software, so we thus annotated the coordinates using labelme and generated a dataset for the training.

   
  <tr>
    <td style="border: none;"><img src="https://github.com/user-attachments/assets/ada1ed50-ead4-4cfa-a3ec-ae5d4cf22b1f" width="300" height="300"></td>
    <td style="border: none;"><img src="https://github.com/user-attachments/assets/64e6ce93-f5a1-4321-9360-5b3a3eeafd1e" width="300" height="300"></td>
  </tr>
</table>

   We used these annotations to generate the coordinates of these images in a JSON file and then used these coordinates and the photos to train our model.

   We also annotated doughnut images to let the model train to differentiate between inductor and doughnut shape.
   <tr>
    <td style="border: none;"><img src="https://github.com/user-attachments/assets/a6bdb070-5dac-43ea-80e7-330c9430ab1d" width="300" height="300"></td>
    <td style="border: none;"><img src="https://github.com/user-attachments/assets/95883884-0287-4b01-87b7-7934db481c33" width="300" height="300"></td>
  </tr>
</table>

5. **Model**:
   ## Faster R-CNN Model

Faster R-CNN is a state-of-the-art object detection framework that combines a Region Proposal Network (RPN) with a Fast R-CNN detector, allowing for efficient and accurate object detection.

### Key Features:
- **Two-Stage Detection**: First, the RPN generates region proposals, and then the detection network classifies and refines these proposals.
- **Backbone Network**: Utilizes ResNet with Feature Pyramid Networks (FPN) for robust feature extraction at multiple scales.
- **Pre-trained Weights**: Trained on the COCO dataset, providing a strong initialization for custom tasks.

### Applications:
Faster R-CNN is widely used in various fields, including autonomous driving, video surveillance, and robotics, making it ideal for detecting objects like **Inductor** and **Donut** in this project.

   






