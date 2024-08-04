# IOS Native Health Data
Analyze & get benefit from iPhone health data for daily life style and better health

## Purpose
The actual purpose of this repo is to fulfil an acadamic task. 
Below are that high level tasks being done here, i.e:

Parsing apple native health data, performing data processing, analysis, gaps, feature engineering, forecasting and finally improving health statistics and life style 
## Background
Since the topic of acadamic task was open so i had many options in the field of ML/AI/DataScience. All i ever wanted is to work on image classification, tagging and GAN's. Image processing tasks were practiced well on a GPU PC, like face tagging via training a basic and CNN and further a YOLO on a large custom data set as i have over 65,000/- facial images in my Google Photos app and nearly 100 are already tagged. So it performed well on a GPU based machine but sadely its taken back and i dont have access to it. Secondly i loved to work on GAN's as back in 2022 someone shared me a VQGAN+CLIP notebook and it was working and played with it but it was black box for me as at that time i was unaware of python and ML. Then in march 2022 i played with MIDJOURNEY V2 via custom deployed notebook and finally tried discord in August-22 on MIDJOURNEY V3.
Due to limitation of GPU (on colab entire RAM is eaten up) i finally ended up in writing a XML parser, analyzing data, doing preprocessing feature engineering and predictions. This reminds me old back yesr 2005 when i wrote a NMEA parser for my yellow eTrex as a sub-part of my BE FYP. Finally after 2 decades i ended up in a more or less similar task,  but the ML part is new here :)
Also my acadamic session was ending on July-31 and i was in an impression that i would be free onwards and made already commitments so i had only 2-3 days for this (minus workplace hours)  

## High Level Workflow
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

## Pre Requisits
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

## References

1
2
3
    

Github repo:
https://github.com/h4harris/IOS_health_data


Enjoy ...    :)
