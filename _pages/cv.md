---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Download PDF

Education
======
* **M.Sc.**, ITMO University, St. Petersburg (online). 2024
* **Professional retraining in Data Science**, University of Artificial Intelligence, Moscow, Russia (online). 2021
* **B.Arch. in Urban Planning**, Saint Petersburg State University of Architecture and Civil Engineering, St. Petersburg, Russia. 2018

Work experience
======
* **Data Scientist / Python Backend.** Apr '22 - . *Metaperson*.
  * Took part in making a pipeline for creating a realistic lip-synchronized videos;
  * Created an API service for DL pipeline based on FastAPI, Celery, Redis and Flower wrapped in a docker-compose;
  * Created a Django web-service with Celery task manager for creating lip-synchronized videos and text-to-speech audiofiles via web-interface;
  * Created a Telegram Bot based on the same Django web-service.
* **Junoir Data Scientist / Python Backend.** Apr '21 - Mar '22. *University of Artificial Intelligence*.
  * Added new algorithms for file processing and continuous support of old ones;
  * Wrote an algorithms for creating datasets for a number of tasks such as classification, segmentation, object detection, etc.;
  * Created a layout of a web interface. Worked in a team with designers and front-end developers for implementation;
  * Wrote and published a documentation for dataset creation process on readthedocs.org.

* **Data Science Intern.** Dec '20 - Mar '21. *University of Artificial Intelligence*.
  * Wrote an algorithms for processing raw data such as images, videos, texts, audio, table data;
  * Wrote a module for creating and loading datasets and using it in the process of training neural network.
  
Skills
======
* Programming
  * Python, Git, Scikit-learn, Keras, OpenCV, NumPy, Pandas, Librosa, Matplotlib, Seaborn. 
* Software
  * PyCharm, Visual Studio Code, Anaconda, Jupyter.
  
Publications
======
  <ul>{% for post in site.publications %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
