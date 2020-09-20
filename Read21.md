# Readings: Django Models [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read21.md)

## Django Tutorial Part 3: Using models:

  - __overview__:
    - Django web applications access and manage data through Python objects referred to as models. 
    - Models define the structure of stored data, including the field types and possibly also their maximum size, default values, selection list options, help text for documentation, label text for forms, etc.
    - The definition of the model is independent of the underlying database — you can choose one of several as part of your project settings. 
 
 - __Model primer__:
   - This section provides a brief overview of how a model is defined and some of the more important fields and field arguments.
   - Model definition: 
     - Models are usually defined in an application's models.py file. 
     - They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata.
   - __Fields__:
     - A model can have an arbitrary number of fields, of any type — each one represents a column of data that we want to store in one of our database tables.
     - Each database record (row) will consist of one of each field value.
   - __Metadata__:
     - You can declare model-level metadata for your Model by declaring class Meta.
   - __Methods__:
     - A model can also have methods.
     - Minimally, in every model you should define the standard Python class method __str__() to return a human-readable string for each object. 
     - This string is used to represent individual records in the administration site (and anywhere else you need to refer to a model instance).
     - Often this will return a title or name field from the model. 
   - __Model management__:
     - Once you've defined your model classes you can use them to create, update, or delete records, and to run queries to get all records or particular subsets of records. 
     - We'll show you how to do that in the tutorial when we define our views.
---
## Django Tutorial Part 4: Django admin site:
  
  - __Overview__:
    - The Django admin application can use your models to automatically build a site area that you can use to create, view, update, and delete records.
    - This can save you a lot of time during development, making it very easy to test your models and get a feel for whether you have the right data.
    - The admin application can also be useful for managing data in production, depending on the type of website.
    
  - __Creating a superuser__:
    - In order to log into the admin site, we need a user account with Staff status enabled. 
    - In order to view and create records we also need this user to have permissions to manage all our objects. 
    - You can create a "superuser" account that has full access to the site and all needed permissions using manage.py.
    - Call the following command, in the same directory as manage.py, to create the superuser.
    
  - __Logging in and using the site__:
    - To login to the site, open the /admin URL (e.g. http://127.0.0.1:8000/admin) and enter your new superuser userid and password credentials (you'll be redirected to the login page, and then back to the /admin URL after you've entered your details).
    - This part of the site displays all our models, grouped by installed application.
    - You can click on a model name to go to a screen that lists all its associated records, and you can further click on those records to edit them. 
    - You can also directly click the Add link next to each model to start creating a record of that type.
    - You will be prompted to enter a username, email address, and strong password.
    
  - __Advanced configuration__:
    - Django does a pretty good job of creating a basic admin site using the information from the registered models:
    - Each model has a list of individual records, identified by the string created with the model's __str__() method, and linked to detail views/forms for editing.
    - By default, this view has an action menu at the top that you can use to perform bulk delete operations on records.
    - The model detail record forms for editing and adding records contain all the fields in the model, laid out vertically in their declaration order. 
    - You can further customise the interface to make it even easier to use. 
---
## A Complete Beginner's Guide to Django - Part 1:
  
  - __Why Django?__
    - Django is a Web framework written in Python.
    - A Web framework is a software that supports the development of dynamic Web sites, applications, and services. 
    - It provides a set of tools and functionalities that solves many common problems associated with Web development, such as security features, database access, sessions, template processing, URL routing, internationalization, localization, and much more.
    - Using a Web framework, such as Django, enables us to develop secure and reliable Web applications very quickly in a standardized way, without having to reinvent the wheel. 
    
  - __Installation__:
    - The first thing we need to do is install some programs on our machine so to be able to start playing with Django.
    - The basic setup consists of installing Python, Virtualenv, and Django.
    - ![img](https://simpleisbetterthancomplex.com/media/series/beginners-guide/1.11/part-1/Pixton_Comic_Basic_Setup.png)
    - Installing Virtualenv: `pip install virtualenv`
    - Installing Django 1.11.4: `pip install django`
    
  - __Starting a New Project__:
    - 1 - django-admin startproject myproject
      - Our initial project structure is composed of five files:
        - __manage.py__: a shortcut to use the django-admin command-line utility.
        - It’s used to run management commands related to our project.
        - We will use it to run the development server, run tests, create migrations and much more.
        - ____init__.py__: this empty file tells Python that this folder is a Python package.
        - __settings.py__: this file contains all the project’s configuration. We will refer to this file all the time!
        - __urls.py__: this file is responsible for mapping the routes and paths in our project. 
        - For example, if you want to show something in the URL /about/, you have to map it here first.
        - __wsgi.py__: this file is a simple gateway interface used for deployment. You don’t have to bother about it. Just let it be for now.
     - 2 - python manage.py runserver
 
 - __Django Apps__:
   - app: is a Web application that does something. An app usually is composed of a set of models (database tables), views, templates, tests.
   - project: is a collection of configurations and apps. One project can be composed of multiple apps, or a single app.
   - ![img](https://simpleisbetterthancomplex.com/media/series/beginners-guide/1.11/part-1/Pixton_Comic_Django_Apps.png)
   - 1 -  To create our first app: django-admin startapp boards
     - let’s first explore what each file does:
      - __migrations/__: here Django store some files to keep track of the changes you create in the models.py file, so to keep the database and the models.py synchronized.
      - __admin.py__: this is a configuration file for a built-in Django app called Django Admin.
      - __apps.py__: this is a configuration file of the app itself.
      - __models.py__: here is where we define the entities of our Web application. The models are translated automatically by Django into database tables.
      - __tests.py__: this file is used to write unit tests for the app.
      - __views.py__: this is the file where we handle the request/response cycle of our Web application.
   - 2 - let’s configure our project to use it, open the settings.py and try to find the INSTALLED_APPS variable:
      - ```
          INSTALLED_APPS = [
            'django.contrib.admin',
            'django.contrib.auth',
            'django.contrib.contenttypes',
            'django.contrib.sessions',
            'django.contrib.messages',
            'django.contrib.staticfiles',

            'boards',
        ]
       ```
    - 3 - Open the views.py file inside the boards app, and add the following code:
        ```
            views.py

            from django.http import HttpResponse

            def home(request):
                return HttpResponse('Hello, World!')
        ```
    - 4 - Now we have to tell Django when to serve this view. It’s done inside the urls.py file:
      ```
            urls.py

            from django.conf.urls import url
            from django.contrib import admin

            from boards import views

            urlpatterns = [
                url(r'^$', views.home, name='home'),
                url(r'^admin/', admin.site.urls),
            ]
      ```
