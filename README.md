# Welcome to Help App Platform
---------------------------------------

This is a guide on how to set up the project on your localhost for development.


## Introduction

Help App Platform is running on Django Web framework and Python programming language.

###### Specific Technologies

1. Django Web Framework(Django version 1.11.6)
2. Django Rest Framework(version 3.7.1)
3. Python 3.6.3

###### Environment Setup

We are assuming that you are using linux based system for your software development. It is recommended that you create
a python virtual environment for this project. Ensure that you have installed python 3.6 on your machine. To create
your python virtual environment run the following command:

- virtualenv -p /usr/bin/python3.6 my_project

The above command will create virtual environment with the name my_project. After creating 
virtual environment, you need to activate the environment by running this command: 

- source my_project/bin/activate

The above command will activate your virtual environment. That's it!

While the virtual environment is still active, time to clone the help project. Run the 
following command:

- git clone https://henrymbuguak@bitbucket.org/muva/help_web.git


**Remember the above command will depend on your bitbucket login username**

After cloning the project, a folder with name help_web will be created. Type the following 
command: **cd help_web** to navigate into the project folder.You need to install project dependencies. Run the following command:

- pip install -r requirements.txt

The above command will install all requirements. The next thing is to configure your database. 
This can be done in the settings.py file.



###### Database Migrations

After sorting your database settings. You need to run migrations, to do this, run the following 
command:

- python manage.py makemigrations help

The above command will create migrations but tables are not created yet. To actually create 
tables in the database, run the following command:

- python manage.py migrate



###### Creating Thumbnails

The last thing you need to do is to install ffmpeg for dealing with videos thumbnails.
To install this on linux run the following command:

- sudo apt-get install ffmpeg

To install this on MacOs run the following command:

- brew install ffmpeg


###### Loading Countries Into The Database

Help mobile application needs countries to operate smoothly. To do this, we are using 
what we call **Fixture** in Django. To load countries into the database, run the 
following command:

- python manage.py loaddata countries.json


###### Online Server Setup

To understand how the online server([helplifes.com](http://helplifes.com/)) is setup. You have to read through this tutorial
[How To Set Up Django with Postgres, Nginx, and Gunicorn on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-16-04)



###### Important Commands

Sometimes you may find yourself in a situation where you need to delete data in your tables. 
This can be achieved by running the following command:

- python manage.py sqlflush | python manage.py dbshell

**The above command is very dangerous because you loose data. Use it at your own RISK**


You may find yourself in situation where you have made changes to your models but when 
you try to run _python manage.py makemigrations_ Django migrations system does not detect 
any changes. Well, Django tracks your migrations in a folder called **migrations**. To overcome 
the problem of no changes detected, run the following commands:

- find . -path "*/migrations/*.py" -not -name "__init__.py" -delete
- find . -path "*/migrations/*.pyc"  -delete

The above command should be used when your project is under development environment. 
Of course there's better ways to solve this. Now you can run your migration commands and 
it should work.


Learn more about [Django Migrations System](https://docs.djangoproject.com/en/1.11/topics/migrations/)