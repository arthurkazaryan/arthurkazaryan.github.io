---
title: "Queue video analysis using object detection"
excerpt: "Using object detection to count the number of people in a queue and sending an alert.<br/><img src='/images/portfolio/queue_analysis/main-500x300.jpg'>"
collection: portfolio
---

<a href="https://github.com/arthurkazaryan/itmo_hackathon" title="GitHub">GitHub Repo</a>

# Overview
The project was made during a Data Product Hack, which was held offline at ITMO University between 3th and 10th September 2022 as part of an AI-powered video analytics track.

The main purpose of the idea is to analyze the number of people standing in a queue, collect data, and notify the personnel when there is a need to call one more cashier.
<p align="center"><img width="500" src="/images/portfolio/queue_analysis/queue_animation.gif"></p>

# Solution
The overall scheme contains two servers:
<ul>
<li>Client's side - a camera with an object detection and a small computer for sending POST data (not in this repository);</li>
<li>Server side - a Django based webserver, which receives an API requests via Django REST framework.</li>
</ul>
<p align="center"><img width="500" src="/images/portfolio/queue_analysis/overall_scheme.jpg"></p>

The client's side should make a POST requests to <b><hostname>:8000/api/v1/post/customers</b> containing the next data:
<ul>
<li>count - the number of people currently in a queue;</li>
<li>warning_flag - True if the number of people exceeds 5;</li>
<li>user - the ID number of a registered user;</li>
<li>camera - the ID number of a camera, which belongs to a registered user;</li>
<li>date - time when the data was sent.</li>
</ul>
When the call is successfully received and processed by Django REST framework, the data is being written into SQL database.

# Result
To manage the list of locations and preview the data received current web server was developed.
<p align="center"><img width="500" src="/images/portfolio/queue_analysis/page_locations.jpg"></p>

Each camera has its own page with all the statistics during the day or week. It gives an opportunity to analyze the number of people visited, 
how many people left the store due to a big queue, etc.
<p align="center"><img width="500" src="/images/portfolio/queue_analysis/page_camera.jpg"></p>

When the camera sends a warning_flag, a message in Telegram Bot appears.
