
<p align="center">
  <img src="scheme.png" width="400" />
</p>

---
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/upb-lea/deep-pmsm/master/LICENSE)

**DEEP learning for Permanent Magnet Synchronous Motor temperatures**. This project aims to estimate temperature sequences inside Permanent Magnet Synchronous Motors from given input sequences, that is, 
currents, voltages, coolant and ambient temperatures, and torque as well as motor speed.
All sensor data is recorded on a testbench.

*Caution: Dataset is anonymized and incomplete in order to meet confidentiality obligations.*

# Getting Started
In order to clone this repo and use as a package in your own python projects, proceed as follows:
```
user@pc:~/projects$ git clone git@github.com:wkirgsn/deep-pmsm.git
user@pc:~/projects$ cd deep-pmsm
user@pc:~/projects/deep-pmsm$ pip install [-e] .
```
Use the "-e" flag in case you wish to edit the package. 
After installing via pip you can simply import this project in python with
```py
import pmsm
```
Alternatively, work with this repo directly if you do not intend to import parts of this project into other projects.

## Dataset
Download the dataset here:
https://www.kaggle.com/wkirgsn/electric-motor-temperature

You can also just click [here](https://www.kaggle.com/wkirgsn/electric-motor-temperature/downloads/electric-motor-temperature.zip/2).
Place the unzipped .csv file in pmsm/data/input/.

# Structure
Data must be available in *pmsm/data/input* - all results of trainings and 
predictions are stored in *pmsm/data/output*. Specific paths are editable in 
*pmsm/preprocessing/config.py* though. Data formatting is dealt with in *preprocessing/*, while hyper parameter tuning 
is conducted with utilities from *opt/*.

Executable python files are located in root package folder *pmsm/*.

Most configurations can be adjusted in *pmsm/preprocessing/config.py*.

# Script files

* **hot_{r,s,c}nn.py**
  + Train a neural network (Recurrent, Self-Normalizing, or Convolutional} with given hyperparameters from config.py
* **hp_tune_{r,c}nn.py**
  + Conduct hyperparameter search via Bayesian Optimization with given hyperparameters from config.py
* **visualize.py**
  + Visualize performance of a certain model, given its UID.
* **hp_vis.py**
  + Visualize results of a certain hyperparameter search, given its UID.

# Citation
This repository is published in order to support reproducability of experiments from the IEMDC 2019 conference paper [Deep Residual Convolutional and Recurrent Neural Networks for Temperature Estimation in Permanent Magnet Synchronous Motors](https://doi.org/10.1109/IEMDC.2019.8785109).
If you are using this code please cite as follows.
```
@INPROCEEDINGS{8785109,
author={W. {Kirchgässner} and O. {Wallscheid} and J. {Böcker}},
booktitle={2019 IEEE International Electric Machines Drives Conference (IEMDC)},
title={Deep Residual Convolutional and Recurrent Neural Networks for Temperature Estimation in Permanent Magnet Synchronous Motors},
year={2019},
volume={},
number={},
pages={1439-1446},
keywords={Machine Learning;Deep Learning;Thermal Management;Permanent Magnet Synchronous Motor;Neural Networks},
doi={10.1109/IEMDC.2019.8785109},
ISSN={},
month={May},}
```
