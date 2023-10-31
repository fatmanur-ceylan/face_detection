# face_detection

## Requirements

## Quick Start and Installation

Build and activate the conda environment.
Add the torch libraries with the specific version of cuda 11.8.
```shell
conda create -n facedetect python=3.10
conda activate facedetect
conda install pytorch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 pytorch-cuda=11.8 -c pytorch -c nvidia
```

**InsightFace Installation**

```shell
cd insightface
pip3 install -r requirements.txt
pip3 install onnxruntime-gpu
pip3 install -v -e python-package/ --no-cache-dir
pip3 install insightface>=0.2.0
```
