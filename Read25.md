# Readings: Django REST Framework & Docker [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read25.md)

## A Beginner's Guide to Docker

  - With Docker it doesn’t matter if you are using a Mac, Windows, or Linux computer anymore.
  - The entire development environment is isolated: programming language, software packages, databases, and more.
  -  Docker is a complex beast under the hood.
  - __Linux Containers__: Docker is really just Linux containers which are a type of virtualization.
  - __Containers vs Virtual Environments__: 
    - Virtual environments are used to isolate Python software packages locally. We can create an isolated box for individual projects so one can use Python 2.7 and Django 1.5 while another can use Python 3.5 and Django 2.1 on the same computer. 
    - But…virtual environments can only isolate Python packages.
    - Also we can’t run a production database or other services within virtual environments.
    
 - __Install Docker__:
    - To install Docker we need to download the desktop app on our computer and create a free account.
    - It should be at least version 19.

            $ docker --version
            Docker version 19.03.5, build 633a0ea
            
   - on Linux, by running the command `sudo pip install docker-compose`. 
      -  The version should be at least 1.24.x.

              $ docker-compose --version
              docker-compose version 1.24.1, build 4667896b
              
 - __Hello, World__: To confirm Docker installed correctly we can run our first command docker run hello-world.  
 - __Images and Containers__:
    - Images and containers are the two fundamental concepts to grasp when you start with Docker.
    - An image is a snapshot in time of what a project contains.
    - A container is a running instance of the image.
   
- __Conclusion__:
    - Docker is a way to run Linux containers
    - Containers are a lightweight alternative to Virtual Machines
    - Dockerfile is a list of instructions for creating an image
    - Images are made up of one or more layers
    - Containers are a running instance of an image
    - docker-compose.yml controls how to run the container
    - Containers are stateless and ephemeral in nature. We can link the local filesystem via volumes but things become more complex with databases
    
---
## Chapter 2: Library Website and API:

  - Django REST Framework works alongside the Django web framework to create web APIs. 
  -  The most important takeaway is that Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.
  
  
  - __Django REST Framework__:
    - Django REST Framework is added just like any other third-party app. 
    - `pipenv install djangorestframework~=3.11.0`.
    - ## config/settings.py
              INSTALLED_APPS = [
                  'django.contrib.admin',
                  'django.contrib.auth',
                  'django.contrib.contenttypes',
                  'django.contrib.sessions',
                  'django.contrib.messages',
                  'django.contrib.staticfiles',

                  # 3rd party
                  'rest_framework', # new

                  # Local
                  'books',
              ]
              
      - create a new api app.
