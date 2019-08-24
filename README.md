# The Pico Project

Object Detection & Text Analytics Made Simple using Pico

![alt text](https://github.com/collabnix/pico/blob/master/images/thepicoproject1.png "My Image")



## What is Pico all about?


Imagine you are able to capture live video streams, identify objects using deep learning, and then trigger actions or notifications based on the identified objects - all using Docker containers. With Pico, you will be able to setup and run a live video capture, analysis, and alerting solution prototype.

![alt text](https://github.com/collabnix/pico/blob/master/images/pico-project-arch.png)

                            

A camera surveils a particular area, streaming video over the network to a video capture client. The client samples video frames and sends them over to AWS, where they are analyzed and stored along with metadata. If certain objects are detected in the analyzed video frames, SMS alerts are sent out. Once a person receives an SMS alert, they will likely want to know what caused it. For that, sampled video frames can be monitored with low latency using a web-based user interface.

The Pico framework uses Kafka cluster to acquire data in real-time. Kafka is a message-based distributed publish-subscribe system, which has the advantages of high throughput and perfect fault-tolerant mechanism. The type of data source is the video that generated by the cameras attached to Raspberry Pi. 


![alt text](https://github.com/collabnix/pico/blob/master/images/pico_in_3_steps.png)


## Offerings

- Pico for AWS
- Pico for On-Premises(Using Swarm & Kubernetes)

## Preparing Your Environment

|Items        |   Link        | Reference  |
| ------------- |:-------------:| -----:|
| Raspberry Pi 3 Model B| [Buy](https://robu.in/product/latest-raspberry-pi-3-model-b-original/ref/60/) | ![Buy](https://github.com/collabnix/pico/blob/master/images/pibox.png) |
| Raspberry Pi Infrared IR Night Vision Surveillance Camera Module 500W Webcam | [Buy](https://robu.in/product/raspberry-pi-infrared-ir-night-vision-surveillance-camera-module-500w-webcam/ref/60/) | ![Buy](https://github.com/collabnix/pico/blob/master/images/picbox2.png/)| 
| 5MP Raspberry Pi 3 Camera Module W/ HBV FFC Cable | [Buy](https://robu.in/product/5mp-raspberry-pi-camera-module-w-hbv-ffc-cable/ref/60) | ![Buy](https://github.com/collabnix/pico/blob/master/images/pibox3.png)| 


## View of Raspberry Pi Stack

![alt text](https://github.com/collabnix/pico/blob/master/images/pico2.png)

## Getting Started - An Easy Way

### Cloning the repository onto Raspberry Pi

```
git clone https://github.com/collabnix/pico
cd pico/deployment/objects/
```

### Execute the producer 

```
python3 producer_camera.py
```

Keep it running.

## Running Kafka on Swarm Cluster on AWS

In order to run Kafka on AWS, you need t2.medium instances which doesn't fall under Free Tier. You will need to use your FREE credits or pay for its usage. Alternatively, for development purpose if you are not concerned about performance, you can use GCP instances.

I assume that you have Docker and Docker Compose installed on one of AWS instance.

### Cloning the Repository

```
git clone https://github.com/collabnix/pico
cd pico/kafka
```

```
docker-compose up -d
```

That's it. Your AWS KAfka cluster is up and running on a single node. For running Apache Kafka on Swarm Mode, refer [this link](https://github.com/collabnix/pico/blob/master/kafka/README.md)

### Building up 

### Cloning the Repository

## Running Image Processor Script(Run on any AWS instance)

```
docker pull ajeetraina/opencv4-python3
```

## Execute the Image Processor Script

```
nohup python3 image_processor.py
nohup python3 consumer.py
```




## Getting Started - The Hard Way

Stage I - [Installing Docker on Raspberry Pi](https://github.com/collabnix/pico/tree/master/getting-started)<br>
Stage II - [Turn Your Raspberry Pi into Night survillience Camera using Docker](http://collabnix.com/turn-your-raspberry-pi-into-low-cost-cctv-surveillance-camerawith-night-vision-in-5-minutes-using-docker/)<br>
Stage III -  [Deploy Apache Kafka on AWS Platform using Docker Swarm](https://github.com/collabnix/pico/blob/master/kafka/README.md)<br>
Stage IV - [Pushing the video frame from Raspberry Pi to Apache Kafka](https://github.com/collabnix/pico/blob/master/kafka/producer-consumer.md) <br>
Stage IV - []() - [Preparing AWS Lambda Deployment Package in Python & Testing Kafka Connect AWS Lambda Connector](https://github.com/collabnix/pico/blob/master/lambda/README.md)<br>



