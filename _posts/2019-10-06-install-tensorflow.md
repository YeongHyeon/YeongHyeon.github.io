---
layout: post
categories: posts
title: Install TensorFlow in Ubuntu
tags: [Setting]
date-string: OCTOBER 06, 2019
---

This post covers how to install the <a href="http://www.tensorflow.org">'TensorFlow'</a> in Ubuntu. This method needs download procedure via web browser [<a href="https://yeonghyeon.github.io/posts/2019-08-19/install-tensorflow.html">Related Post<a>].

### 1. Install CUDA

First, download CUDA from <a href="https://developer.nvidia.com/cuda-toolkit-archive">CUDA Toolkit Archive</a>. In this repository, CUDA-10.0 is used (<a href="https://developer.nvidia.com/cuda-10.0-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal">CUDA Toolkit 10.0 Download Page</a>). Then, enter the following commands for installing CUDA.

``` sh
sudo dpkg -i cuda-repo-ubuntu1804-10-0-local-10.0.130-410.48_1.0-1_amd64.deb
sudo apt-key add /var/cuda-repo-10-0-local-10.0.130-410.48/7fa2af80.pub
sudo apt-get update
sudo apt-get install cuda
```

### 2. Install cuDNN

After installing CUDA, one more procedure is needed that is installing cuDNN from <a href="https://developer.nvidia.com/cudnn">NVIDIA cuDNN</a>. Please move to <a href="https://developer.nvidia.com/cudnn">NVIDIA cuDNN</a> page, login, and select 'Download cuDNN v7.6.4 (September 27, 2019), for CUDA 10.0'. Then, download 'cuDNN Runtime Library for Ubuntu18.04 (Deb)'. If you want to install developer version, download 'cuDNN Developer Library for Ubuntu18.04 (Deb)' additionally. When the downloading procedure is finished, enter the following commands.

```sh
sudo dpkg -i libcudnn7_7.6.4.38-1+cuda10.0_amd64.deb
sudo dpkg -i libcudnn7-dev_7.6.4.38-1+cuda10.0_amd64.deb
```

Finally you need to add the environmental paths to '.bashrc' using following commands.

```sh
echo "export PATH=/usr/local/cuda-10.0/bin:$PATH" >> .bashrc
echo "export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64:$LD_LIBRARY_PATH" >> .bashrc
echo "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/extras/CUPTI/lib64" >> .bashrc
```

Then, you may reboot your PC and type 'nvidia-smi' to your terminal as below. You can confirm that your GPU and GPU-drivers work well.

``` console
yeonghyeon@Ubuntu1804:~$ nvidia-smi
Sun Oct  6 16:40:34 2019       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 410.48                 Driver Version: 410.48                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 108...  Off  | 00000000:19:00.0 Off |                  N/A |
|  0%   37C    P8     9W / 250W |      2MiB / 11178MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   1  GeForce GTX 108...  Off  | 00000000:1A:00.0 Off |                  N/A |
|  0%   34C    P8     8W / 250W |     18MiB / 11177MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   2  GeForce GTX 108...  Off  | 00000000:67:00.0 Off |                  N/A |
|  0%   34C    P8    10W / 250W |      2MiB / 11178MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   3  GeForce GTX 108...  Off  | 00000000:68:00.0 Off |                  N/A |
|  0%   34C    P8     8W / 250W |     18MiB / 11177MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
+-----------------------------------------------------------------------------+
```

### 3. Install TensorFlow

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

### Reference
<a href="https://www.tensorflow.org/install">Install TensorFlow</a><br>
<a href="https://developer.nvidia.com/cuda-toolkit-archive">CUDA Toolkit Archive</a><br>
<a href="https://developer.nvidia.com/cudnn">NVIDIA cuDNN</a>
