# YOLOv7-custom data set training in google collab



## Installation


<details><summary> <b>Expand</b> </summary>

# apt install required packages
apt update
apt install -y zip htop screen libgl1-mesa-glx

# pip install required packages
!pip install --upgrade setuptools pip --user
!pip install --ignore-installed PyYAML
!pip install Pillow

!pip install nvidia-pyindex
!pip install --upgrade nvidia-tensorrt
!pip install pycuda

!pip install protobuf<4.21.3
!pip install onnxruntime-gpu
!pip install onnx>=1.9.0
!pip install onnx-simplifier>=0.3.6 --user
# open google collab and follow the instructions 
## Mount your google drive to collab
     from google.colab import drive
     drive.mount("/content/gdrive")

## git clone official yolov7 to drive
 
    !git clone https://github.com/WongKinYiu/yolov7.git
 
## get .pt of your choice from official yolov7

     !wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-tiny.pt

## label your dataset using labelimg and create trian and val folder for 
    training and paste it in data folder of yolov7
# TO train model 
    !python train.py --device 0 --batch-size 16 --epochs 100 --img 640 640 --data data/custom_data.yaml --hyp data/hyp.scratch.custom.yaml --cfg cfg/training/yolov7-       tiny.yaml --weights yolov7-tiny.pt --name yolov7-custom

# TO run the trained model 
## For image put a image in yolov7 folder
    !python detect.py --weights best.pt --conf 0.25 --img-size 640 --source 1.jpg.jpeg


# If any error check yaml version
      import yaml
      yaml.__version__
      !pip install --upgrade pyyaml==5.3.1
