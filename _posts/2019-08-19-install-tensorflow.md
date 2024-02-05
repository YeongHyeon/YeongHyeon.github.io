---
layout: post
categories: posts
title: Install TensorFlow in Ubuntu - Terminal Only
tags: [Setting]
date-string: AUGUST 19, 2019
---

This post covers how to install the <a href="http://www.tensorflow.org">'TensorFlow'</a> in Ubuntu. This method does not need other download procedure via web browser (only using terminal).

### 1. Install CUDA (CUDA 10)

``` sh
echo "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/extras/CUPTI/lib64" >> .bashrc

# Add NVIDIA package repositories
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-repo-ubuntu1804_10.0.130-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1804_10.0.130-1_amd64.deb
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64/nvidia-machine-learning-repo-ubuntu1804_1.0.0-1_amd64.deb
sudo apt-get update
sudo apt install ./nvidia-machine-learning-repo-ubuntu1804_1.0.0-1_amd64.deb
sudo apt-get update

# Install NVIDIA driver
sudo apt-get install --no-install-recommends nvidia-driver-410
# Reboot. Check that GPUs are visible using the command: nvidia-smi

# Install development and runtime libraries (~4GB)
sudo apt-get install --no-install-recommends \
	cuda-10-0 \
	libcudnn7=7.6.0.64-1+cuda10.0  \
	libcudnn7-dev=7.6.0.64-1+cuda10.0


# Install TensorRT. Requires that libcudnn7 is installed above.
sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends libnvinfer-dev=5.1.5-1+cuda10.1
```

### 2. Install TensorFlow

``` sh
# install virtual environment
sudo apt update
sudo apt install python3-dev python3-pip
sudo pip3 install -U virtualenv

# make virtual environment
virtualenv --system-site-packages -p python3 ./{name of virtual environment} # for example venv

# activate virtual environment
source ./{name of virtual environment}/bin/activate

# install tensorflow
pip install --upgrade pip
pip install tensorflow-gpu=={TensorFlow version} # for example 1.14.0
```

### 3. Install other python libraries

``` sh
pip install matplotlib
pip install scipy
pip install sklearn
```

### Reference
<a href="https://www.tensorflow.org/install">Install TensorFlow</a>
