# Welcome to Online Shopping Cart
---------------------------------------

This is a guide on how to set up the project on your localhost for development.


## Introduction

Online Shopping Cart is running on Django Web framework and Python programming language.

###### Specific Technologies

1. Django Web Framework(Django version 2.0)
2. Python 3.6.3

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

- git clone https://github.com/henrymbuguak/Shopping-Cart-Using-Django-2.0-and-Python-3.6.git


After cloning the project, a folder with name shopping_cart will be created. Type the following 
command: **cd shopping_cart** to navigate into the project folder.You need to install project dependencies. Run the following command:

- pip install -r requirements.txt

The above command will install all requirements. The next thing is to configure your database. 
This can be done in the settings.py file.



###### Database Migrations

After sorting your database settings. You need to run migrations, to do this, run the following 
command:

- python manage.py makemigrations 

The above command will create migrations but tables are not created yet. To actually create 
tables in the database, run the following command:

- python manage.py migrate


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