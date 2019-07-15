# Classification of Bearing Faults
## Introduction
Bearing is one of the most widely used machine element in rotating machines. The figure below shows a typical rolling element bearing, which consists of the cage, ball, inner race and outer race.

![Bearing](https://github.com/zerothphase/CWRU/blob/master/Figures/Bearing.PNG)
Image from: [link](https://arxiv.org/abs/1901.08247)

Failure of bearing can cause serious breakdown of a machine. Therefore, bearing fault detection and classificaiton has been one of the important research area in engineering. The bearing dataset from the [Case Western Reserve University (CWRU) Bearing Data Center](https://csegroups.case.edu/bearingdatacenter/home) is commonly used as the benchmark for bearing fault classification algorithm, which contains **vibration signal data** of normal and faulty bearings. 
Vibration signals of 4 classes of bearings are available in this dataset, namely:
- normal bearing without fault (N)
- bearing with single point defect at the inner raceway (IR)
- bearing with single point defect at the outer raceway (OR)
- bearing with single point defect at the ball (B). 

Single point defects of different diameters (0.007 ~ 0.028 Inches) are manufactured to the bearings artificially.

In this dataset, vibration signal data of normal bearing, bearing with drive end (DE) and fan end (FE) bearing defects was collected at a sampling rate of 12 kHz using accelerometers. The collected data is stored as Matlab files and each Matlab file contains 
between ~120k to ~240k sample points. Besides that, vibration signals of drive end bearing defect are also collected at 48 kHz. The figures below show one example of each class.

<img src="https://github.com/zerothphase/CWRU/blob/master/Figures/signal_N.png" width="400"> <img src="https://github.com/zerothphase/CWRU/blob/master/Figures/signal_B.png" width="400"> 
<img src="https://github.com/zerothphase/CWRU/blob/master/Figures/signal_IR.png" width="400"> <img src="https://github.com/zerothphase/CWRU/blob/master/Figures/signal_OR.png" width="400">

## Overview
1D CNN has been sucessfully applied to fault classification based on signal data in some papers 
(e.g. [[1]](https://doi.org/10.1155/2017/8617315), 
[[2]](https://www.researchgate.net/publication/304550799_Real-Time_Motor_Fault_Detection_by_1D_Convolutional_Neural_Networks)). 
The main advantage of using a 1D CNN is that manual feature extraction like spectrum analysis, statistical features and so on is not
required. After normalization, the signal data can be directly feed into the 1D CNN for training.

In this repo, simple two layers and 3 layers 1D CNN are experimented and achieved similar performance 
(99%+ accuracy) as recent papers, as summarized by [[3]](https://arxiv.org/pdf/1901.08247.pdf).

Helper functions for data cleaning and preprocessing are written in the `helper.py` module, whereas helper functions for training using Pytorch Framework are written in the `train_helper.py` module.

The notebook [`CWRU_Dataset.ipynb`](https://nbviewer.jupyter.org/github/zerothphase/CWRU/blob/master/CWRU_Dataset.ipynb) shows the training process and the trained model is saved in the `./Model` folder.
