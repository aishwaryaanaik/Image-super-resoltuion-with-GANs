#  Image Super-Resolution using SRGAN  
This project includes converting low-resoltuion images to high resolution images using **SRGAN**.
## Introduction  
Image Super-Resolution (SR) is a critical task in computer vision that reconstructs **high-resolution (HR) images** from their **low-resolution (LR) counterparts**.  
It has wide applications in:  
-  **Medical imaging** (enhancing scans)  
-  **Remote sensing** (sharper satellite imagery)  
- **Digital media** (improving video/photo quality)  

Traditional methods (bicubic interpolation, simple CNNs) fail to recover fine textures, producing blurred images.  
We leverage **Super-Resolution GANs (SRGAN/ESRGAN)** with **Residual-in-Residual Dense Blocks (RRDB)** to generate sharper and more realistic images.  

---

##  Objectives  
- Develop a **deep learning-based SRGAN** model.  
- Upscale low-resolution images by a factor of **4×**.  
- Preserve **fine textures, edges, and details** while keeping images natural.  
- Evaluate performance using both **quantitative (PSNR, SSIM)** and **qualitative (visual comparison)** methods.  



## Methodology  
<img width="900" height="400" alt="Screenshot 2025-08-25 153251" src="https://github.com/user-attachments/assets/d401e033-18fc-47d8-b35e-f5b8fe545680" />

1. **Dataset**  
   - Source: Kaggle *Image Super-Resolution dataset*.  
   - Paired LR and HR images for training, validation, and testing.  

2. **Preprocessing**  
   - Downsampled HR → LR using bicubic interpolation.  
   - Resized LR to **1/4th dimensions of HR**.  
   - Normalized images to `[0,1]`.  

3. **Model Architecture**  
   - **Generator**: Based on **RRDB blocks** (Residual-in-Residual Dense Blocks).  
   - **Upsampling**: PixelShuffle layers ×2 for 4× upscaling.  
   - **Discriminator**: Relativistic GAN discriminator to improve perceptual quality.  
   - **Loss Functions**:  
     - Pixel loss: MSE  
     - Perceptual loss: VGG-based  
     - Adversarial loss  

4. **Training**  
   - Optimizer: Adam  
   - Loss minimized: MSE + perceptual + adversarial  
   - Checkpoints saved as `.pth`  

5. **Inference**  
   - Pretrained generator loads LR input.  
   - Outputs super-resolved HR image (4× upscaled).  

6. **Evaluation Metrics**  
   - **PSNR (Peak Signal-to-Noise Ratio)** – pixel-level similarity.  
   - **SSIM (Structural Similarity Index)** – structure & texture similarity.  

7. **Visualization**  
   - Display **LR vs SR vs HR images** side-by-side.  
   - Compare sharpness, edges, textures.  


##  Results  

- Model achieves **high PSNR and SSIM** values, showing strong reconstruction ability.  
- Visual results demonstrate clear improvements in fine details and textures compared to LR inputs.  

## Co-authors
- Annapurna,Tejaswini Sattikar


