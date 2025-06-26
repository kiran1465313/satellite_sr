# 🛰️ Satellite Image Super-Resolution using ESRGAN

This project applies **ESRGAN** (Enhanced Super-Resolution GAN) using the [BasicSR framework](https://github.com/XPixelGroup/BasicSR) to upscale low-resolution satellite images.

---

## 🗂️ Folder Structure
├── datasets/  
│ └── satellite/  
│ ├── HR/ # High-resolution images  
│ └── LR/ # Corresponding low-resolution images  
├── experiments/  
│ └── satellite_esrgan/  
│ ├── models/  
│ │ └── net_g_latest.pth # Trained Generator model  
│ ├── training_states/  
│ │ └── latest.state # Optimizer & iteration state (optional for resume)  
├── options/  
│ └── satellite_esrgan.yml # Configuration YAML  
├── results/  
│ └── satellite_esrgan_test/ # Output from test  
├── basicsr/  
│ └── ... # BasicSR core code  


```python
#install these dependencies
!pip install basicsr
!pip install facexlib gfpgan
```


#🏋️ Training
1. Place HR and LR images in:
```python
datasets/satellite/HR/
datasets/satellite/LR/
```
2.If needed, generate LR from HR:
```python
import os
import cv2

def make_lr_from_hr(hr_dir, lr_dir, scale=4):
    os.makedirs(lr_dir, exist_ok=True)
    for filename in os.listdir(hr_dir):
        if filename.lower().endswith(('.png', '.jpg', '.tif')):
            hr_path = os.path.join(hr_dir, filename)
            img = cv2.imread(hr_path)
            if img is None:
                continue
            h, w = img.shape[:2]
            lr = cv2.resize(img, (w // scale, h // scale), interpolation=cv2.INTER_CUBIC)
            cv2.imwrite(os.path.join(lr_dir, filename), lr)
``` 
3.Start training:
```python
#on colab if running on terminal remove "!" at front
!python basicsr/train.py -opt options/satellite_esrgan.yml --launcher none
```
 
