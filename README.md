# Full Stack Django Cloud Dev Project
### _A cloud-hosted web-app for a car dealership's car reviewal platform_

This repo contains the code for a Django [web application](https://sr-django-capstone.eu-de.mybluemix.net/djangoapp/) hosted in the IBM Cloud. 

#### Background
I developed the application as part of the final [Capstone Project](https://www.coursera.org/learn/ibm-cloud-native-full-stack-development-capstone?specialization=ibm-full-stack-cloud-developer) in the 10-course [IBM Full Stack Cloud Developer Professional Certificate](https://www.coursera.org/professional-certificates/ibm-full-stack-cloud-developer) on Coursera. The general architecture and idea for the application was provided by Coursera, as well as most of the design and layout. 


#### Project Requirements
The general idea is to build a website that allows users to select one of *Best Car*'s dealerships (a fictional company) in the US to view other users' reviews of the dealership's cars, as well as submit their own reviews. The site also needed basic functionality such as a navigation bar and static "about" and "contact" pages. The website had to be built with the Python-Django full stack web development framework and be deployed with Red Hat Openshift/Kubernetes on the IBM Cloud.

#### Architecture
![Application architecture model](capstone-project-model.png)
_Application architecture_

The dealership and review data is located in an IBM Cloudant database, while data about users and cars is in a simple SQLite database. In order to access data from IBM Cloudant, I wrote three IBM Cloud Functions which were accessible through an API. 

Each review is analysed by IBM Watson in order to display the review's general sentiment (negative, neutral, positive). 

#### Setup 
To run the application locally, follow these steps:
- ```cd server/```

Install the required Python packages
- ```python -m pip install -r requirements.txt```

If having trouble with the Pillow package, try installing the following:
- ```brew install jpeg libjpeg```

Run the development server: </br>
- ```python manage.py createmigrations```
- ```python manage.py migrate```
- ```python manage.py runserver```

Create a new superuser:
- ```python manage.py createsuperuser```
- Log in via the admin site (just add `/admin` at the end of the url)

Push to IBM Cloud Foundry:
- Install the IBM Cloud CLI and the cloud foundry plugin
- Configure the `manifest.yml` file
- `ìbmcloud cf push`
