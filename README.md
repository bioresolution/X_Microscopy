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

Challenges

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
2. Environment called XMicro2 works perfectly well for this modified code structure, accessed via anaconda
3. The code has successfully been run, however produces no significant output on their own given data, as well as urs. 2 possible reasons are: 1) Failre of the code 2) The model they pretrained is ineffective

## Future Direction

1. Start from training the model completely on our data, basically decreasing dependency on their data
2. Seeking inspiration from provided model structure to build our own custom Gen AI model



# Original code README

* The folder of UR-Net-8 contains the MU-SRM reconstruction code, and change to this folder to perform wf->MU-SRM.git 
* The folder of X-Net contains the F-SRM reconstruction code, and change to this folder to perform wf+MU-SRM->F-SRM.


## Instructions
When you use this code, please change the corresponding folder in the code to yours, i.e., the data path in the train, evaluate, and test functions of the train.py, and in the main function of the main.py. 

The parameter of --phase is to alternative the state of training or test, set as train for training and set as test for test.
+ For training:
```bash
python main.py --phase train
```
+ For test: 
```bash
python main.py --phase test
```
The parameter of --same_input_size is to alternative fixed input size or flexible input size during the training stage. If you want to run the code with fixed input size during the training stage, you shold set the value of --same_input_size as True, otherwise, set the value of --same_input_size as False.
+ For training or fine-tuning with fixed input size: 
```bash
python main.py --phase train --same_input_size True
```
+ For training or fine-tuning with flexible input size: 
```bash
python main.py --phase train --same_input_size False
```
The script of evaluate.py is used to evaluate the performances of SRM reconstruction, which is based on the realized verison of python. When you use it, please change the corresponding folder to yours.
## Pretrained models
We provide the trained models to reproduce the results that presented in our paper. 

+ [Google Drive](https://drive.google.com/drive/folders/1tVtzCAihlcHfcBRTTPW4S3fWuTT1xVEU?usp=drive_link)

For detailed technical details, please see our paper and the released code.

### Citation

If you use this method or this code in your research, please cite as:

    @inproceedings{XuleiKanshichao-2022,
    title={Deep learning enables STORM-like superresolution image reconstruction from conventional microscopy},
    author={Lei Xu, Shichao Kan, Xiying Yu, Yuxia Fu, Yiqiang Peng, Yanhui Liang, Yigang Cen, Changjun Zhu, Wei Jiang},
    booktitle={},
    pages={},
    year={2023}
    }

### Acknowledgments
This code is written based on the tensorflow framework of pix2pix. 

### License
This code is released for academic research / non-commercial use only. This project is covered under the MIT License.
