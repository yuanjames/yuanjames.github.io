---
layout: post
comments: false
title : The note for installing a series of requirements for deep learning
description: Installation of CUDA, cuDNN, Pytorch, and Tensorflow
categories: instruction
date: 2021-11-21 12:00:00
---

I have experienced many times that installing and configuring new environment (including python, libraries, CUDA etc), this is very ANNOYING. So, I am here to make some notes for convinience in future.

Operation system: Ubuntu

1.Vscode - Go to the https://code.visualstudio.com/, download the Debian version, use the command `sudo dpkg -i <file>.deb` to install it.

2.Anaconda - Go to the https://docs.anaconda.com/anaconda/install/linux/ , download the Debian version.
The following commands are used to verfiy and install the Anaconda. During the installation, the offical recommend you to accept the default install location. 


        sha256sum /path/filename
        bash ~/Downloads/Anaconda3-2020.02-Linux-x86_64.sh

        conda create -n name python=3.xx
        conda activate name
 

3.CUDA Toolkit（Nvidia Official, rather than from Pytorch) - 'CUDA is a software layer that gives direct access to the GPU's virtual instruction set and parallel computational elements'. When you install CUDA Toolkit, you will get a Nvidia driver: for your GPUs, GPU-accelerated libraries, debugging and optimization tools, a C/C++ compiler, and a runtime library. See below commands for Ubuntu 20.04 and CUDA 11.03. Then, you will find the driver and CUDA are installed by `nvidia-smi`.
    
        wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
        sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
        wget https://developer.download.nvidia.com/compute/cuda/11.3.0/local_installers/cuda-repo-ubuntu2004-11-3-local_11.3.0-465.19.01-1_amd64.deb
        sudo dpkg -i cuda-repo-ubuntu2004-11-3-local_11.3.0-465.19.01-1_amd64.deb
        sudo apt-key add /var/cuda-repo-ubuntu2004-11-3-local/7fa2af80.pub
        sudo apt-get update
        sudo apt-get -y install cuda
 
 From here, you can download Pytorch by `conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch` to run your code over the GPU(s), because the CUDA/cuDNN files required by PyTorch come with it already (p.s. this cudatoolkit is not related to the official one to some degree, or in other words Pytorch works alone only required driver).


Additionally, you may find the `nvcc -V` gives your error. You could deal with it by adding some libraries paths `export PATH=$PATH:/usr/local/cuda/bin` to `.bashrc` file.


4.cuDNN - The NVIDIA CUDA® Deep Neural Network library. If you need to use Tenrsorflow, it means you have to install cuDNN libraries. Please find the approprite version from https://developer.nvidia.com/rdp/cudnn-archive.
        
        Download the cuDNN (https://developer.nvidia.com/rdp/cudnn-archive): cuDNN Runtime Library for Ubuntu20.04 x86_64 (Deb), cuDNN Developer Library for Ubuntu20.04 x86_64 (Deb), cuDNN Code Samples and User Guide for Ubuntu20.04 x86_64 (Deb)
        
        sudo dpkg -i libcudnn8_8.2.4.15-1+cuda11.4_amd64.deb 
        sudo dpkg -i libcudnn8-dev_8.2.4.15-1+cuda11.4_amd64.deb
        sudo dpkg -i libcudnn8-samples_8.2.4.15-1+cuda11.4_amd64.deb

        In this way, you do have to configure the path becasue dpkg ubuntu system tool will help to install this in system with the path.

