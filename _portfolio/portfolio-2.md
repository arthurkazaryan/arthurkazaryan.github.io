---
title: "Creating artificial speaking human beings using lip-synchronized animation"
excerpt: "The project was developed at one of Korpus.io's startups called Metaperson.<br/><img src='/images/portfolio/lipsync/main-500x300.png'>"
collection: portfolio
---

# Overview
In some cases of the process of shooting videos, which can be a movie, a TV-show, or just a videoblog, there might be a necessity for localization on the number of different languages. Also, some people might be unreachable for various number of reasons and there is no opportunity for them to take part in the process of shooting again. In that case, lip-synch technology might be the right option to use.

While working as urban planner the tasks can be divided by routine (manual) side of work, which contains some analysis, drawing, calculating, and creative, which contains making concepts of a new parts of area, districts, cities. 
It is pretty easy to imagine how to write a program for doing routine stuff, but it is hard to write a program for tasks that require creative work such as making concepts.
The purpose of this project was to create a tool for urban planners which can allow them to create concepts with much more ease.

# Scheme
The idea of the project is to use a video of a human’s face as the first input data, and an audiofile of a human’s speech as the second input data. The result would be a video of a human’s face with lip-sync animation of what was told in an audiofile.
<p align="center"><img width="100%" src="/images/portfolio/lipsync/scheme_animation.gif"></p>
<p align="center">An overall scheme</p>
In the “Mystery box” the number of open-source technologies are used with some major improvements to increase the output quality.

# Result
The result can be seen below.
<p align="center"><img width="100%" src="/images/portfolio/lipsync/result_animation.gif"></p>
<p align="center">An overall scheme</p>

# API service
In order to have access to the technology an API service based on FastAPI was created. Due to the long processing time a Celery task manager was implemented to take care of the tasks received. 

<p align="center"><img width="700" src="/images/portfolio/lipsync/scheme_api.jpg"></p>
<p align="center">Scheme of an API service</p>

There are 4 links available for requests:
<ul>
<li><b>api/v1/lipsync/push</b> - POST request {'audio': "audio_file", 'video': "video_file"} - files to process;</li>
<li><b>api/v1/lipsync/terminate</b> - POST request {'task_id': "uuid"} - a celery task id to terminate;</li>
<li><b>api/v1/lipsync/status</b> - GET request {'task_id': "uuid"} - get the status of a celery task;</li>
<li><b>api/v1/lipsync/download</b> - GET request {'file_path': "str"} - path to a file to download.</li>
</ul>
