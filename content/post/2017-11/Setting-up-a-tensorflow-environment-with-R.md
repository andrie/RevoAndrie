---
author: "Andrie de Vries"
title: "Setting up a tensorflow environment with R"
type: "post"
draft: "false"
date: "2017-11-22T06:00:00Z"
categories: 
- "R"
- "TensorFlow"
tags:
- "package"
summary: "Setting up a tensorflow environment with R"
thumbnail: "images/2017-11/tensorflow.jpg"
---


Create a new conda env

```bash
conda create -n tensorflow python=3.6 numpy scipy matplotlib scikit-learn h5py
```

Switch to Anaconda prompt

```bash
activate tensorflow
```

Note that your promt changes to include the name of the active conda environment

```bash
(tensorflow) C:\Users\apdev>
```

Now use `conda install` to install the prerequisites

```
conda install numpy scipy matplotlib scikit-learn h5py
```

Then make sure the packages installed correctly

```bash
conda list

(tensorflow) C:\Users\apdev>conda list
# packages in environment at C:\tools\Anaconda3\envs\tensorflow:
#
ca-certificates           2017.08.26           h94faf87_0
certifi                   2017.11.5        py36hb8ac631_0
cycler                    0.10.0           py36h009560c_0
freetype                  2.8                  h51f8f2c_1
h5py                      2.7.0            py36hfbe0a52_1
hdf5                      1.10.1               h98b8871_1
icc_rt                    2017.0.4             h97af966_0
icu                       58.2                 ha66f8fd_1
intel-openmp              2018.0.0             hcd89f80_7
jpeg                      9b                   hb83a4c4_2
libpng                    1.6.32               h140d38e_4
matplotlib                2.1.0            py36h11b4b9c_0
mkl                       2018.0.0             h36b65af_4
numpy                     1.13.3           py36ha320f96_0
openssl                   1.0.2m               h093b818_1
pip                       9.0.1            py36h226ae91_4
pyparsing                 2.2.0            py36h785a196_1
pyqt                      5.6.0            py36hb5ed885_5
python                    3.6.3                h3b118a2_4
python-dateutil           2.6.1            py36h509ddcb_1
pytz                      2017.3           py36h1d3fa6b_0
qt                        5.6.2           vc14h6f8c307_12  [vc14]
scikit-learn              0.19.1           py36h53aea1b_0
scipy                     1.0.0            py36h1260518_0
setuptools                36.5.0           py36h65f9e6e_0
sip                       4.18.1           py36h9c25514_2
six                       1.11.0           py36h4db2310_1
sqlite                    3.20.1               h9eeafa9_2
tornado                   4.5.2            py36h57f6048_0
vc                        14                   h2379b0c_2
vs2015_runtime            14.0.25123           hd4c4e62_2
wheel                     0.30.0           py36h6c3ec14_1
wincertstore              0.2              py36h7fe50ca_0
zlib                      1.2.11               h8395fce_2
```


