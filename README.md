# Density Based Traffic Light Control System
The main aim of the proposed system is to constantly monitor the vehicle density present in all parts of the 4 lanes.
The basic flow of operation is as follows: collection of vehicle density data from the roads; next is to send the same data to the device which compares the density of the 4 lanes with each other. In this model, the cameras are used to detect the presence of any vehicle in that part of the lane. When detected it sends a triggered output to Arduino Board which is the heart of the project. Then  Arduino analyses the number of such triggered outputs from the set of cameras placed on each 4 lane and correspondingly adds some seconds for the green light for the lane where the density of vehicles is more than others respectively.

The working of the project is divided into three steps:

• If there is traffic at all the signals, then the system will work normally by controlling the signals one by one. 

• If there is no traffic near a signal, then the system will skip this signal and will move on to the next one. For example, if there is no vehicle at signal 2, 3 and currently the system is allowing vehicles at signal 1 to pass. Then after signal 1, the system will move on to signal 4 skipping signal 2 and 3.

• If there is no traffic at all the 4 signals, then also the system will work normally by controlling the signals one by one. 

# Proposed Model

**Vehicle Detection Module:**

The proposed system uses YOLO (You only look once) for vehicle detection, which provides the desired accuracy and processing time. A custom YOLO model was trained for vehicle detection, which can detect vehicles of different classes like cars, bikes, tractors, heavy vehicles (buses and trucks), and rickshaws.
YOLO is a clever convolutional neural network (CNN) for performing object detection in real-time. The algorithm applies a single neural network to the full image, and then divides the image into regions and predicts bounding boxes and probabilities for each region. These bounding boxes are weighted by the predicted probabilities. YOLO is popular because it achieves high accuracy while also being able to run in real-time. With YOLO, a single CNN simultaneously predicts multiple bounding boxes and class probabilities for those boxes.


![image](https://github.com/user-attachments/assets/47add30b-afac-4168-87bf-0fa0841d2d63)

<p align="center">
Figure 1
</p>

So basically ***Figure1*** shows that there are three cameras which captures the real time video on the signals respectively for their lane then the captured video is sent to the laptop for processing then the system processes the video and detects the number of vehicles using Object Detection. 

![image](https://github.com/user-attachments/assets/dce412b5-7078-4a7d-b996-8e6047cb29f6)

<p align="center">
Figure 2
</p>

Then after detecting the number of vehicles present in the 3 cameras our algorithm finds the lane where the density of vehicles is more than the others.After finding the more densed lane,the data is then sent to the IOT device i.e in our case is Arduino Board.The Arduino Board then adds some more seconds to the green light of the signal where the density of vehicles noted was high as shown in ***Figure2***.

So,for our dataset we have gathered images from Google.

For labeling our images we have used ROBOFLOW,a Computer Vision developer framework for better data collection to preprocessing,and model training techniques.

For training our model we have created a custom model using YOLOV5 custom model and trained it using Google Colab.

![image](https://github.com/user-attachments/assets/db2be81a-9452-4493-ae6c-0f3a4046e217)
![image](https://github.com/user-attachments/assets/0e59d64a-23d0-4bcc-baaa-a980c2e4f607)

<p align="center">
Figure 3
</p>

Above ***Figure3*** shows test images on which our vehicle detection model was applied. The left side of the figure shows the original image and the right side is the output after the vehicle detection model is applied on the image, with bounding boxes and corressponding labels.

# Steps

**1.** Install and import all the dependencies required from **`imagedetection.ipynb`**

**2.** Assemble our Dataset from Roboflow

**3.** Train Our Custom YOLOv5 model

(For more detailed explanation visit https://colab.research.google.com/github/roboflow-ai/yolov5-custom-training-tutorial/blob/main/yolov5-custom-training.ipynb#scrollTo=X7yAi9hd-T4B)

**4.** Run the **`traffic_lights.ino`** file in Arduino IDE.

> [!NOTE]
> Connect all the LED Pins as given in **`traffic_lights.ino`** file

(We have used [cvzone](https://pypi.org/project/cvzone/) library to connect Python code to Arduino Board.

**5.** Run the **`imagedetection.ipynb`** file.

# Results

![image](https://github.com/user-attachments/assets/e861b0ff-c575-475a-be04-f1316f72016c)

![image](https://github.com/user-attachments/assets/21b6b6dd-fd8c-4958-9214-b4e854171362)






