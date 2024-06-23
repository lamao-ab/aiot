# A TinyML Object Detection Model
<br/> 

## 1. Introduction

## 2. Training Scripts

See the YOLOv5-v8 Docs and tensorflowlite tutorials for full documentation on training, testing and deployment.

To Train, Validate and Test YOLOv5 models please refer to: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]()

To Train, Validate and Test YOLOv8 models please refer to: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]()

To Train, Validate and Test TFLite 2 models (efichientdet-d1, ssd mobilenet fpnlite, faster rcnn resnet50 v1) please refer to : [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]()

## 3. Deploy on Raspberry Pi 
<details>
<summary>Update the Raspberry Pi</summary>

On a termonal run the command to update the Raspberry Pi:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Then, enable the camera interface on raspberry-pi:
```
sudo raspi-config
```
Select the Interfaces tab and Enable the camera interface. and reboot the Raspberry Pi.

</details>

<details>
<summary>Download this repository and create virtual environment</summary>

Tap the command to clone this repository:

```
git clone https://github.com/lamao-ab/tinyml-object-detection-models.git
```

rename the folder to "wkspace" and then enter into it:

```
mv tinyml-Object-Detection-models wkspace
cd wkspace
```

Install virtualenv :

```
sudo pip install virtualenv
```

Then, create and activate the "wkspace-env" virtual environment, which will contain all the package libraries for this environment:

```
python -m venv wkspace-env
```

```
source wkspace-env/bin/activate
```
</summary>
</details>

### 3.1 Pytorch models

<details>
<summary>yolov5</summary>
  
Install ultralytics pip package
```
pip install ultralytics
```

Clone repo and install requirements.txt.

```
git clone https://github.com/ultralytics/yolov5  
cd yolov5
pip install -r requirements.txt 
```
Run Inference   
``` 
python detect.py --data /home/pi/wkspace/SOD-2/data.yaml --source /home/pi/wkspace/SOD-2/test/images/ --weights /home/pi/wkspace/custom_models/yolov5n.py  --imgsz 640 --conf 0.25
```
</details>

<details>
<summary>yolov8</summary>

Install ultralytics </summary>  
```
pip install ultralytics==8.0.20
pip install --upgrade ultralytics
```

Run Inference>

```
cd yolov8
yolo task=detect mode=predict source= /home/pi/wkspace/SOD-2/test/images/  model=/home/pi/wkspace/custom_models/yolov8n.pt data=/home/pi/wkspace/SOD-2/data.yaml imgsz=640 conf=0.25 save=True 
```
</details>



### 3.1 TensorFlow Lite models

<details>
<summary>Install TensorFlow Lite dependencies and OpenCV</summary>
  
```
pip install tensorflow opencv-python protobuf==3.20.*
```
</details>

<details>
<summary>Run the TensorFlow Lite model</summary>
Run the real-time webcam detection script by executing the following command from inside the /home/pi/wkspace directory.
demo is a folder that contain the model file and label classes file. 
  
```
python detection_webcam_voice.py --modeldir=demo
```
</details>

## 4. Nighttime low illumination image enhancement using Dark/Bright channel priors

This script is a python implementation [5](https://github.com/spmallick/learnopencv/tree/master/Improving-Illumination-in-Night-Time-Images/python) of Nighttime low illumination image enhancement with single image using bright/dark channel prior [Paper](https://jivp-eurasipjournals.springeropen.com/articles/10.1186/s13640-018-0251-4).
https://github.com/spmallick/learnopencv/tree/master/Improving-Illumination-in-Night-Time-Images/python

<details>
<summary>Install dependencies and run image enhacement script</summary>
  
```
pip install numpy opencv-contrib-python
```

```
python night_images.py
```
</details>

## References

- [1] https://github.com/ultralytics/ultralytics
- [2] https://github.com/ultralytics/yolov5
- [3] https://www.tensorflow.org/lite/guide/python
- [4] https://colab.research.google.com/github/EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi/blob/master/Train_TFLite2_Object_Detction_Model.ipynb
- [5] https://github.com/spmallick/learnopencv/tree/master/Improving-Illumination-in-Night-Time-Images/python


