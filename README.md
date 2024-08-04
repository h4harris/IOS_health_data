# IOS Native Health Data
Analyze & get benefit from iPhone health data for daily life style and better health

## Purpose
The actual purpose of this repo is to fulfil an academic task. 
Below are that high level tasks being done here, i.e:

Parsing apple native health data, performing data processing, analysis, gaps, feature engineering, forecasting and finally improving health statistics and life style {data wrangling}

## Problem

1.  The biggest problem is the academic FP, that I have to complete in next 3 days …
    Ha ha …  kidding …
    
2.  There is a list of problems but the problem with highest severity was that I was getting notifications from watch since last year and then warnings from health app that my Vo2max value critically low, it went down to 35 and for my age (41) it should remain >40 as a minimum (lowest) threshold. Went to cardiologist and he took some tests and said that I don’t remember this value Vo2max as I studied during specialization but don’t remember now. So when I enrolled in this academic session I did some EDA on my health data (end of May-2024) and found several trends / routines that I was repeating over and over (daily), so I applied several walk / running profiles based on mistakes (identified by EDA process) and in July Vo2Max was 44.7

3.  List goes on …  predicting my vitals for next quarter based on my last year’s data


## High Level Workflow

Below are that high level tasks being done here, i.e:

  * Extract Data from Apple Health App's
  * Make exported data accessible to colab
  * Read data in colab
  * Filter Desired Data
  * Perform Detailed EDA & Pre Processing
  * Import & Analyze gpx's
  * Some Experimental Features
  * Analyze Results and find gaps
  * Perform Feature Engineering
  * Perform Predictions
  * Apply refined routine on daily life

## Pre Requisites
  * Required python libs (see lib.txt)
  * Health profile is pre setup
  * Workouts exists
  * Apple watch (Watch OS 11/+)
  * IOS 17/+ devices
  * Apple Health Data (except cda export)
  * Colab
 


## Setup and Usage
1.  Open 'Health' app   
![IMG-20240804-WA0004](https://github.com/user-attachments/assets/911102e5-e3d6-48ab-ac93-ba427afb6d4a)

2.  Click on profile button as shown in below picture

![IMG-20240804-WA0005](https://github.com/user-attachments/assets/5b008470-7c2c-4c69-aa7c-9f67e2be21c4)

4.  Click on 'Export All Health Data' as shown in below picture

![IMG-20240804-WA0006](https://github.com/user-attachments/assets/446048f9-83c0-41d6-8167-553a9a3491f7)

6.  Click on 'Export'as shown in below picture

![IMG-20240804-WA0007](https://github.com/user-attachments/assets/e1fefbd5-729d-49e5-8284-6b4d699330fa)

4.  Processing,  depends on data size

![IMG-20240804-WA0008](https://github.com/user-attachments/assets/041eaff0-6fc2-4cb1-b20e-479f3892dfe3)

6.  Choose Export location, i prefer to store a master copy in 'files', then share to desired location

![IMG-20240804-WA0009](https://github.com/user-attachments/assets/079040d7-2152-42ee-ae52-49f75c0c18df)

8.  View file on iPhone or colab or any OS,  below screenshot is the directory tree of exported data (Win11pro)

![image](https://github.com/user-attachments/assets/4e49aa49-937f-4bdf-a5dc-ac9731951b95)

10.  Here we are interested in 'export.xml' and gps tracklogs i.e: 'workout-routes' folder

11.  Upload this folder to google drive or set local machine's directory as path in python code

13.  For any directory path issues while playing py,  below is the reference directory tree

![image](https://github.com/user-attachments/assets/127e5857-2276-4dce-b162-63c3be662baf)

14.  Play / Interpret py master file,  'Apple_Aug_2024_export.ipynb

15.  Play / Interpret other py scripts, i.e
  * apple_health_data_parsing_export.ipynb
  * Feature_Engineering.ipynb
  * Feature_Engineering_2.ipynb
  * plot_geotagged_pic.ipynb
  * gpx_plotter.ipynb

## Screenshots (Demo)

1.  Weekly Workouts (in my case only walk and running)

![image](https://github.com/user-attachments/assets/8c935ccf-e97d-4cda-aab5-b48fb3d50bc0)

2.  Workout type vs Energy

![image](https://github.com/user-attachments/assets/e135cedd-174d-4447-9e1e-29d1d8c7c9d5)

3.  Monthly distance including walk / run.

![image](https://github.com/user-attachments/assets/e9c42ed9-7000-4161-bbf4-55b7d7dccadb)


4.  Inputing a native apple health file (xml/compressed) and after parsing, exporting it (passthrough) to csv for basic users (download option)

![image](https://github.com/user-attachments/assets/3be844a8-51ca-4e4f-ba17-e0080e4f46d8)

5.  Feature Engineering {showing only (1 of 41) activities as a demo, i.e:
    HKQuantityTypeIdentifierAppleExerciseTime

![Screenshot 2024-08-04 204956](https://github.com/user-attachments/assets/18d7d226-b19f-4032-8e2b-1cff5077b748)

    
![image](https://github.com/user-attachments/assets/ca4e5387-70a8-4303-ac74-83db999e2081)

6.  Comparisons of different developments including this, IOS native and Strava

![image](https://github.com/user-attachments/assets/a0b7fed4-d4d2-4c4d-9d37-73e8c161ff27)

![image](https://github.com/user-attachments/assets/20cb4ddf-ec07-4f52-bbff-063da8615776)





## Libraries

import matplotlib.pyplot as plt

import seaborn as sns

import xml.etree.ElementTree as ET

import pandas as pd

import datetime as dt

import plotly.express as px

import plotly.graph_objects as go

from plotly.subplots import make_subplots

from IPython.display import display

import seaborn as sns

import xml.etree.ElementTree as ET

import gradio as gr

import joblib

import pandas as pd

import osrad

import pandas as pd


import xmltodict

import zipfile

import numpy as np

from matplotlib.dates import DateFormatter

import seaborn as sns

import matplotlib.pyplot as plt

import statsmodels.api as sm

from gpxplotter import create_folium_map, read_gpx_file, add_segment_to_map

import folium

import PIL

from PIL.ExifTags import TAGS, GPSTAGS

import datetime

## Coding references / help taken from:

1.  This document made the core function possible, The Element Tree

https://docs.python.org/3/library/xml.etree.elementtree.html

3.  IOS forums

IOS API documentation, support.apple.com , discussions.apple.com

5.  For playing with native gpx's
 
https://pypi.org/project/folium/
https://pypi.org/project/gpxplotter/

##Author Thoughts:

Since the topic of academic task was open so i had many options in the field of ML/AI/DataScience. All i ever wanted is to work on image classification, face tagging and GAN's. Image processing tasks were practiced well on a GPU PC, like face tagging via training a basic and CNN and further a YOLO on a large custom data set as i have over 65,000/- facial images in my Google Photos app and nearly 100 are already tagged. So it performed well on a GPU based machine but sadly its taken back and i dont have access to it. Secondly i loved to work on GAN's as back in 2022 someone shared me a VQGAN+CLIP notebook and it was working and played with it but it was black box for me as at that time i was unaware of python and ML. Then in march 2022 i played with MIDJOURNEY V2 via custom deployed notebook and finally tried discord in August-22 on MIDJOURNEY V3.
Due to limitation of GPU (on colab entire RAM is eaten up) i finally ended up in writing a XML parser, analyzing data, doing preprocessing feature engineering and predictions. The basic parser i wrote back in May-24 during EDA sessions, that saved a lot of time for now and i continued it today. This reminds me old back year 2005 when i wrote a NMEA parser for my yellow eTrex as a sub-part of my BE FYP. Finally after 2 decades i ended up again in a more or less similar task,  but the ML part is new here :)
Also my academic session was ending on July-31 and i was in an impression that i would be free onwards and made already commitments so i had only 2-3 days for this (minus workplace hours)  

I remember old days (2005) when i played with eTrex on serial db9 interface for BE FYP, Android was very weak that time and Symbian S60v3 was near its end of life. The google API, PHP...
It took me 3 months in old days to interface native Google earth with MySQL and HTTP server to show live location of eTrex and my S60v3 mobile.
Since then, no coding just basic scripting for SQA.
Python and its plugins {components, libraries} made life extremely easy.
In 2022 at my workplace we built a system for foreign client and it utilizes Elastic Search via Kibana, AL models can also be utilized here. The next step that will make this small project very useful is its integration with elasticsearch / Kibana. 

I realized that data analysis is difficult, especially when we do not have in depth understanding of data and its (domain or work products),  so before opening IDE do read documentation and understand the problem without any doubts otherwise, we end up in verification and validation dilemma.

Github Repo:

https://github.com/h4harris/IOS_health_data

Enjoy ...    :)



👋 Hi, I’m @h4harris

👀 I’m interested in Software QA

🌱 I’m currently learning ML/AI

💞️ I’m looking to collaborate on Github and Gitlab

📫 Connect with me on LinkedIn, Twitter, IG, Discord as #h4harris

📫 https://www.instagram.com/h4harris/

📫 h4harris@gmail.com

😄 He

⚡ Singularity is near
