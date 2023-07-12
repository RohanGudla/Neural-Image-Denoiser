
# Denoising with GAN
[Paper](https://uofi.box.com/shared/static/s16nc93x8j6ctd0ercx9juf5mqmqx4bp.pdf) | [Video](https://www.youtube.com/watch?v=Yh_Bsoe-Qj4)

## Introduction

Animation movie companies like Pixar and Dreamworks render their 3D scenes using a technique called Pathtracing, which enables them to create high-quality photorealistic frames. Pathtracing involves shooting 1000’s of rays into a pixel randomly (Monte Carlo), which will then hit the objects in the scene. Based on the reflective property of the object, the rays reflect, refract, or get absorbed. The colors returned by these rays are averaged to get the color of the pixel, and this process is repeated for all the pixels. Due to the computational complexity, it might take 8-16 hours to render a single frame.

We are proposing a neural network-based solution for reducing 8-16 hours to a couple of seconds using a Generative Adversarial Network. The main idea behind this proposed method is to render using a small number of samples per pixel (let's say 4 spp or 8 spp instead of 32K spp) and pass the noisy image to our network, which will generate a photorealistic image with high quality.

# Demo Video [Link](https://www.youtube.com/watch?v=Yh_Bsoe-Qj4)

[![Demo Video](https://img.youtube.com/vi/Yh_Bsoe-Qj4/0.jpg)](https://www.youtube.com/watch?v=Yh_Bsoe-Qj4)

#### Table of Contents

* [Installation](#installation)
* [Running](#running)
* [Dataset](#dataset)
* [Hyperparameters](#hyperparameter)
* [Results](#results)
* [Improvements](#improvements)
* [Credits](#credits)

## Installation

To run the project, you will need:
 * Python 3.5
 * TensorFlow (v1.1 or v1.0)
 * PIL
 * [CKPT FILE](https://uofi.box.com/shared/static/21a5jwdiqpnx24c50cyolwzwycnr3fwe.gz)
 * [Dataset](https://uofi.box.com/shared/static/gy0t3vgwtlk1933xbtz1zvhlakkdac3n.zip)

## Running

Once you have all the dependencies ready, follow these steps:

1. Download the dataset and extract it to a folder named 'dataset' (ONLY if you want to train, not needed to run).

2. Extract the CKPT files to a folder named 'Checkpoints'.

3. Run `main.py`:
   ```bash
   python3 main.py
   ```

4. Go to the browser, if you are running it on a server then [ip-address]:8888. If you are on your local machine, use localhost:8888.

## Dataset

We selected random 40 images from Pixar movies, added Gaussian noise of different standard deviations, resulting in 1000 images for the training set. For validation, we used 10 completely different images from the training set and added Gaussian noise. For testing, we had both added Gaussian images and real noisy images.

## Hyperparameters

* Number of iterations - 10K
* Adversarial Loss Factor - 0.5
* Pixel Loss Factor - 1.0
* Feature Loss Factor - 1.0
* Smoothness Loss Factor - 0.0001

## Results

### 3D Rendering Test Data
![3D rendering test data](https://github.com/manumathewthomas/CS523Project3/blob/master/result1.PNG)

### Real Noise Images
![Real noise images](https://github.com/manumathewthomas/CS523Project3/blob/master/result2.png)

### CT-Scan
![CT-Scan](https://github.com/manumathewthomas/CS523Project3/blob/master/result3.PNG)

## Improvements

* Increase the number of iterations to 100K.
* Train the network for different types of noise.
* Make it work on a real-time app.

## Credits

* [SRGAN](https://arxiv.org/pdf/1609.04802.pdf)
* [Image De-raining using conditional generative adversarial network](https://arxiv.org/pdf/1701.05957.pdf)
* [Creating photorealistic images from Gameboy camera](http://www.pinchofintelligence.com/photorealistic-neural-network-gameboy/)
* [CS20SI](cs20si.stanford.edu)
* [CS231n](https://cs231n.github.io/)


Please note that this project is intended for personal experimentation and educational purposes.