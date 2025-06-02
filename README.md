# NEURAL-STYLE-AND-HIGH-RESOLUTION-IMAGE-UPSCALLING
# 🎨 Neural Style Transfer & Neural Doodles

Neural Style Transfer (NST) is a deep learning technique that fuses the **content of one image** with the **style of another**, creating mesmerizing results that mimic artistic styles. Originally introduced by *Gatys et al.* in ["A Neural Algorithm of Artistic Style"](https://arxiv.org/abs/1508.06576), NST has since evolved into various powerful implementations.

---

## 🧠 Implementing Neural Style Transfer

NST can be implemented using frameworks like **PyTorch** and **TensorFlow**.

### 🔧 PyTorch-based NST Workflow

1. **Image Preprocessing**
2. **Model and Loss Definition**
3. **Style Transfer Optimization**

PyTorch tutorials provide comprehensive guides to achieve this using VGG models.

---

## 📸 Examples

### 🎯 Single Style Transfer

| Content Image | Style Image |
|---------------|-------------|
| ![blue moon lake](https://raw.githubusercontent.com/titu1994/Neural_Style_Transfer/master/images/inputs/content/blue-moon-lake.jpg) | ![starry night](https://raw.githubusercontent.com/titu1994/Neural_Style_Transfer/master/images/inputs/style/starry_night.jpg) |

**Output (100 Iterations, INetwork):**  
![styled result](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/output/Blue-Moon-Lake_at_iteration_100.jpg?raw=true)

**DeepArt.io Output (1000 Iterations + MRF):**  
![deepart result](https://raw.githubusercontent.com/titu1994/Neural_Style_Transfer/master/images/output/DeepArt_Blue_Moon_Lake.jpg)

---

### 🌀 Style Interpolation

| Content: *Dipping Sun* | Style: *Misty Mood (Leonid Afremov)* |
|------------------------|--------------------------------------|
| ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/inputs/content/Dipping-Sun.jpg?raw=true) | ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/inputs/style/misty-mood-leonid-afremov.jpg?raw=true) |

| Style=1, Content=1000 | Style=1, Content=1 | Style=1000, Content=1 |
|----------------------|--------------------|------------------------|
| ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/output/DippingSun3.jpg?raw=true) | ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/output/DippingSun2.jpg?raw=true) | ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/output/DippingSun1.jpg?raw=true) |

---

### 🎨 Multiple Style Transfer

**Content: Blue Moon Lake**  
**Styles:** Starry Night (Van Gogh) + Red Canna (Georgia O’Keeffe)

| Starry Night | Red Canna |
|--------------|-----------|
| ![](https://raw.githubusercontent.com/titu1994/Neural_Style_Transfer/master/images/inputs/style/starry_night.jpg) | ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/inputs/style/red-canna.jpg?raw=true) |

| 1.0 / 0.2 | 1.0 / 0.4 | 1.0 / 1.0 |
|----------|-----------|-----------|
| ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/output/blue_moon_lake_1-0_2.jpg?raw=true) | ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/output/blue_moon_lake_1-0_4.jpg?raw=true) | ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/output/blue_moon_lake_1-1_at_iteration_50.jpg?raw=true) |

---

### ⚙️ Combined Techniques

Applied: Multi-scale NST + Mask Transfer + Super Resolution + Sharpening + Denoising.

| Content | Style | Mask |
|---------|-------|------|
| ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/inputs/content/ancient_city.jpg?raw=true) | ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/inputs/style/blue_swirls.jpg?raw=true) | ![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/inputs/mask/ancient-city.jpg?raw=true) |

**Final Output:**  
![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/output/ancient_city_multiscale.jpg?raw=true)

---

## 🖌 Neural Doodles

### Renoir Style + Content  
![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/neural_doodle/generated/renoit_new.png?raw=true)

### Monet Style + Sketch  
![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/neural_doodle/generated/monet_new.png?raw=true)

### Van Gogh Style + Sketch  
![](https://github.com/titu1994/Neural-Style-Transfer/blob/master/images/neural_doodle/generated/van%20gogh.png?raw=true)

---

## ⚙️ Model Details (VGG-16)

- Uses `conv5_2` instead of `conv4_2` for **content loss**.
- Option to initialize from `content` or `noise`.
- **AveragePooling2D** or **MaxPooling2D**.
- Maintains image aspect ratio and rescaling logic.

---

## 💡 INetwork Enhancements

- All VGG-16 layers used for style inference.
- Style weight scaling.
- Geometric layer weighting, gram matrix activation shift, correlation chaining.
- Optimizations for **multi-style**, **multi-mask**, and **masked** transfers.

---

## ✅ Features

- ✅ Style Transfer, Neural Doodles, Color Transfer, Masked Transfer
- ✅ CLI & GUI support
- ✅ Multiple styles and masks
- ✅ Log folders per experiment
- ✅ Compatible with Windows & Linux

---

## 🖥️ Requirements

- Python with Keras (1.0.7+)
- Theano / TensorFlow backend
- CUDA + cuDNN (recommended for GPU)
- Numpy, Scipy, PIL, Scikit-image, h5py

---

## 🚀 Performance (on NVIDIA 980M GPU)

| Image Size | Time/Epoch |
|------------|------------|
| 400×400    | 8–10 sec   |
| 512×512    | 15–18 sec  |
| 600×600    | 24–28 sec  |

Multi-style or multi-mask transfers increase time linearly but are optimized via gradient exclusion.

---

## 🎬 INetwork Demo

![demo](https://raw.githubusercontent.com/titu1994/Neural-Style-Transfer/master/images/Blue%20Moon%20Lake.gif)

---

## 🧾 Usage Notes

- VGG weights are cached in `~/.keras/models/`.
- Easily experiment with different styles, content weights, and pooling types.
- For multi-style: select all style images & pass weights space-separated.

---
