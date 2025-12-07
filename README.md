
# **`EviRCOD: Evidence-Guided Probabilistic Decoding for Referring Camouflaged Object Detection`**

# Requirements
Python v3.9, Pytorch 2.5.1, Cuda 12.8, TensorboardX 2.0, opencv-python

# Get Start
### 1. Data Preparation
- Download [R2C7K](https://pan.baidu.com/s/1LHdqpD3w24fcLb_dbR6DyA) dataset with access code ```2013``` on Baidu Netdisk. Our method is based on this dataset for experimentation.
```   
├── R2C7K  
    ├── Camo  
        ├── train                # training set of camo-subset with 64 categories.  
        └── test                 # tesing set of camo-subset with 64 categories.  
    ├── Ref          
        ├── Images               # all images of ref-subset with 64 categories.
        ├── RefFeat_ICON-R       # all object representations of ref-subset with 64 categories.  
        └── Saliency_ICON-R      # all foreground maps of ref-subset with 64 categories.  
```
- Update the 'data_root' param with your R2C7K location in ```train.py```, ```infer.py``` and ```test.py```.

### 2. Training
- Download the pre-trained weights of [pvtv2]: https://pan.baidu.com/s/1czmAayK9N5bW2HqrBDHWaw code: EviR on Baidu Netdisk, and place them  in your custom floder.
- Run `python train.py` to train the model.
- You can also download the our pre-trained [EviR.pth]: https://pan.baidu.com/s/10UtikqOnWzyGHxI8Ij-o2g code: EviR on Baidu Netdisk.

### 3. Testing
- After training, run `python test.py` to evaluate the performance of EviRCOD.

### 4. Inference
- After training, run `python infer.py` to generate the prediction maps of EviRCOD.
- You can also download our prediction maps : https://pan.baidu.com/s/1oU18MDWG6BuyyFdaoOkOzQ code: EviR on Baidu Netdisk.

