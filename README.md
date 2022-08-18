# Image Sampler

- Introduction
- Windows
- Image Quality Assessment
- Libraries
	- PySimpleGui
	- Pillow
	- PyTorch
	- PyTorch Image Quality
	- Open Computer Vision

## Introduction
This program is written in Python and uses a variety of libraries to open, read, view, and manipulate images.  Its purpose is to take a sample of a collection of images and filter out poor quality images using two methods of image quality assessment.

It prompts the user to enter a file path to a folder containing images.  The user chooses a percent for the sample size.  They also choose a fast or slow mode which determines the level of image quality filtering.

Once the sample is created, an image viewer opens which allows the user to browse samples, create more samples, or save a sample.

The acceptable image file types are **jpg, png, bmp, tiff, and tif**.

## Windows
**Collection Picker:**  This window allows the user to browse for a folder or enter a file path.  A sample is created using the given percentage and run-mode (fast or slow).  Slow mode uses blur and BRISQUE scores to filter out poor quality images.

**Image Viewer:**  This window allows the user to browse their samples.  From here, they can either choose to create another sample or save one.  The sample will be saved in the original collection's folder.

## Image Quality Assessment
**Blur Score**  This is implemented with the Open Computer Vision library.  This is the only image quality assessment that runs in fast mode.  To get the blur score, a laplacian operation is performed on each pixel in the image.  Then, the variance of the resulting values is obtained.  This value determines how similar each pixel is overall.  In a blurry image, colors and edges blend together resulting in a low variance.

**Low variance == More blurry**

**BRISQUE:**  Blind/Referenceless Image Spatial QUality Evaluator is a model for computing an image quality score.  This assessment is done based on predetermined values which indicate good image quality.  It is used alongside the blur score when running in slow mode.

**Low BRISQUE score == Higher quality**

## Libraries
**[PySimpleGui:](https://www.pysimplegui.org/en/latest/)**  This library is used to create the user interface.  It builds upon the tkinter, Qt, Remi, WxPython libraries.  The first step in creating the UI is to make a layout and use that layout to create a window.  Next, you read the window and use a loop to wait for events like a button press.

**[Pillow:](https://python-pillow.org/)**  AKA 'Python Imaging Library'.  This library is used to open and manipulate images.

**[PyTorch:](https://pytorch.org/docs/stable/index.html)**  This library is a used to create a tensor from image data.  A tensor is a generic n-dimension array.  A tensor is needed when calculating the BRISQUE scores for image quality assessment.


**[PyTorch Image Quality:](https://piq.readthedocs.io/en/latest/)**  This library is used to calculate the BRISQUE scores for image quality assessment.

**[Open Computer Vision:](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)**  This library is used to read image data and perform an image quality assessment on the blurriness of an image.

## Citations
```
@misc{clark2015pillow,  
title={Pillow (PIL Fork) Documentation},  
author={Clark, Alex},  
year={2015},  
publisher={readthedocs},  
url={https://buildmedia.readthedocs.org/media/pdf/pillow/latest/pillow.pdf}  
}

@article{paszke2017automatic,
  title={Automatic differentiation in PyTorch},
  author={Paszke, Adam and Gross, Sam and Chintala, Soumith and Chanan, Gregory and Yang, Edward and DeVito, Zachary and Lin, Zeming and Desmaison, Alban and Antiga, Luca and Lerer, Adam},
  year={2017}
}

@misc{piq,
  title={{PyTorch Image Quality}: Metrics and Measure for Image Quality Assessment},
  url={https://github.com/photosynthesis-team/piq},
  note={Open-source software available at https://github.com/photosynthesis-team/piq},
  author={Sergey Kastryulin and Dzhamil Zakirov and Denis Prokopenko},
  year={2019},
}

@misc{2015opencv,  
title={Open Source Computer Vision Library},  
author={OpenCV},  
year={2015},  
}
```
