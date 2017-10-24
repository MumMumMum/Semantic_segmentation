### Semantic Segmentation (Scene Understanding)
______________
Basic idea of this project would be to assign a pre-defined value to every pixel.With this we achieve segmentation of image. 
For this project we are going to do segmentation of road images labeling the road part of image using [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php).  

### Deep Learning approach of FCN 
To do this segmentation of image we will use **FCN (Fully Convolution Network)**.  
The whole architecture is planned on this paper presented by [ UCBerkley ](https://people.eecs.berkeley.edu/~jonlong/long_shelhamer_fcn.pdf)   


![ FCN UP_Scaling_Merging ](https://github.com/MumMumMum/Semantic_segmentation/blob/master/imgs/img_0032_upscaling_and_merging.png?raw=true)  


The idea of building FCN is that it takes a pre trained network which can classify images and then retain the spatial info by replacing the last layer(simple loggit which averages the signal value and classifies the images) using 1X1 conv layer and then decode the image back.  

### Building FCN from pre trained network: 
  - Replace fully connected layers with the 1x1 convolution layers 
     - These help in retaining spatial information of the image  
  - Introduce up-sampling by using transposed convolution layers. 
     - This is like decoding from encoded information. 
     - More of  deconv 
  - Add skip connections. 
     - These help in reducing the over fitting of a model. 
     
![ image encoder decoder ](https://github.com/MumMumMum/Semantic_segmentation/blob/master/imgs/1%20Li8osvpQE-s0AYO8cPumFQ.png?raw=true)   

### Training:
Used AWS P2.x to train the model.
Epoch 50
Learning rate 0.0005
Batch Size 12
Keep_prob 0.5

     
### Model Output
![ 1 ](https://github.com/MumMumMum/Semantic_segmentation/tree/master/runs/run2/runs/1508737489.8759882/um_000036.png?raw=true) 

![ 2 ](https://github.com/MumMumMum/Semantic_segmentation/tree/master/runs/run2/runs/1508737489.8759882/um_000039.png?raw=true) 

![ 3 ](https://github.com/MumMumMum/Semantic_segmentation/tree/master/runs/run2/runs/1508737489.8759882/um_000054.png?raw=true) 

![ 4 ](https://github.com/MumMumMum/Semantic_segmentation/tree/master/runs/run2/runs/1508737489.8759882/um_000024.png?raw=true) 

Link to processed video attached in GitHub [here](https://github.com/MumMumMum/Semantic_segmentation/tree/master/runs/run2/runs/1508737489.8759882/sem_seg.mp4) 

### Future enhancements: 
* I should try to run the training on [City scape dataset](https://www.cityscapes-dataset.com/) which has 29 odd data labels.
* I can add logs, Tensor summarize and view the results in Tensor board.
* I need to take video input and run segmentation on video and display output on the go. For this I need to save and load model.


*********
### Udacity Readme 

### Introduction 
In this project, you'll label the pixels of a road in images using a Fully Convolutional Network (FCN).

### Setup
##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)
##### Dataset
Download the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

### Start
##### Implement
Implement the code in the `main.py` module indicated by the "TODO" comments.
The comments indicated with "OPTIONAL" tag are not required to complete.
##### Run
Run the following command to run the project:
```
python main.py
```
**Note** If running this in Jupyter Notebook system messages, such as those regarding test status, may appear in the terminal rather than the notebook.

### Submission
1. Ensure you've passed all the unit tests.
2. Ensure you pass all points on [the rubric](https://review.udacity.com/#!/rubrics/989/view).
3. Submit the following in a zip file.
 - `helper.py`
 - `main.py`
 - `project_tests.py`
 - Newest inference images from `runs` folder
 
 ## How to write a README
A well written README file can enhance your project and portfolio.  Develop your abilities to create professional README files by completing [this free course](https://www.udacity.com/course/writing-readmes--ud777).
