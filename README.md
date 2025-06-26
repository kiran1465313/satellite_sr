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
!pip install basicsr
!pip install facexlib gfpgan
```
