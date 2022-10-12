---
title: "Licence plate detection API with web service"
excerpt: "Detecting cars and licence plates using web interface.<br/><img src='/images/portfolio/licence_plate/main-500x300.jpg'>"
collection: portfolio
---

<a href="https://github.com/arthurkazaryan/licence_plate_detection" title="GitHub">GitHub Repo</a>

The project is made as part of a deep learning course at ITMO University. The goal is to train and deploy a NN model for licence plate recognition.

# Dataset and training
The dataset was downloaded from Open Images Dataset v6 using self written script, based on OIDv6 package. 
The main difference is that OIDv6 doesn't allow to download images, containing both "Car" and "Vehicle licence plate" classes on a single picture.
In order to solve the problem, a new script was written to only download images, which contain both classes.
The script can be found [here](https://github.com/arthurkazaryan/licence_plate_detection/tree/main/dataset)

Yolov7 was chosen for the project for its speed and accuracy benchmarks. 
It took almost 3 hours and 55 epochs to train on a dataset containing 4000 images.
<p align="center"><img width="500" src="/images/portfolio/licence_plate/detection_animation.gif"></p>
<p align="center">Result of a trained yolov7 model</p>

# Building an API
<p align="center"><img width="100%" src="/images/portfolio/licence_plate/api_main.jpg"></p>
The detection module is wrapped around Fast API service. The main task of the module is to receive a POST request, containing an image or video data
{'upload_file': <image/video>} , process it, and return a json-type data, which contains the following:
<ul>
    <li>date: datetime;</li>
    <li>vehicle_type: str;</li>
    <li>color: str;</li>
    <li>number: str;</li>
    <li>vehicle: list;</li>
    <li>plate: list.</li>
</ul>

<p align="center"><img width="500" src="/images/portfolio/licence_plate/api_scheme.jpg"></p>
<p align="center">The scheme of an API service</p>

# Django web service
<p align="center"><img width="100%" src="/images/portfolio/licence_plate/django_main.jpg"></p>

In order to use the API a django-based web service was created. After authentication, it allows the user to upload images with cars,
send them to an API (must be launched. Otherwise, throws an error in the interface), process the result and save it into SQL database.
All the processed images are saved in user's profile and can be accessed anytime.

<p align="center"><img width="100%" src="/images/portfolio/licence_plate/django_view.jpg"></p>
