# X_Microscopy

## Paper Overview
1. X-microscopy enables STORM-like superresolution microscopy image reconstruction from wide-field images with input-size flexibility
2. X-Microscopy was trained using samples of various subcellular structures, to generate prediction models capable of producing images of comparable quality to STORM-like images
3. It enables multicolour superresolution image reconstructions, and facilitates superresolution image reconstruction from different conventional microscopic systems
4. X-Microscopy is a computational tool comprising of two deep learning subnets, UR-Net-8 and X-Net

## Model Archtecture
1. UR Net
Input: Wide Field Images
Output: MU-SRM(Mimic-undersampled SRM)
Model Training: Loss function between U-SRM(undersampled SRM k=10000 from N-STORM) and MU-SRM
Architecture: Comprises of an encoder with 8 convolutional layers and a decoder with 8 deconvolutional layers
2. X-Net
Input: Wide Field Images and MU-SRM
Output: XM1 and XM2 concatenated to XM3
Model Training: Loss function between XM3 and Ground Truth images(SRM images)
Architecture: X-Net was designed with 2 encoders and 2 decoders.

## Challenges
1. Creating an environment for running the code
The original code was written in much older library versions, leading to deprecated functions and dependencies
Dependencies and Versions were not correctly listed
The code was also not intuitively structured
Solution: Creation of a new environment with the latest library version, Comprehensive updation of the code 

2. Linking the correct path for data collection and generation
Input structure not outlined in README
Data provided by them was itself not in the correct format and non-intuitively arranged
Solution: Identified sections of the code for input and functions were marked manually

## Results
After putting in months of hard work and having figured out how to generate results from the model, BOTH the models gave an EMPTY image or a black image as a result

## Present Status
1. The entire Code has been updated to suit the latest versions of all libraries used
2. Environment called *XMicro2* works perfectly well for this modified code structure, accessed via anaconda
3. The code has successfully been run, however produces no significant output on their own given data, as well as urs. 2 possible reasons are: 1) Failre of the code 2) The model they pretrained is ineffective

## Future Direction
1. Start from training the model completely on our data, basically decreasing dependency on their data
2. Seeking inspiration from provided model structure to build our own custom Gen AI model
