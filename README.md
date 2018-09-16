# citadel


## What is it all about?
We bring to you one of its kind crowd contributed portal. 
For the students, by the students and of the students. 
It acts as a one stop platform for all the learning that you will need.
Share, learn and go.
Currently the workpattern is this, people contibute using the upload button, this dumps the file in media/unapproved.
Using the approve page authorised people can add the papers.


## Getting Started: 
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

The following packages are required on a linux machine to compile and use the software package.

```
python3
pip3
```

### Dependencies
```
course.json --> File that lists all the courses
profs.json --> File that maps uids of Profs to their Names
```

### Installing

Deploying citadel is fairly simple. Just issue the following commands on a linux machine
You need crontab installed at your system for the required cronjobs to work

```
git clone https://github.com/devclub-iitd/citadel.git
cd citadel
python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt
mkdir media
mkdir media/database
mkdir media/unapproved
mkdir media/bulk
cd make_folder
python make_folder.py
cp -r DATA/* ../media/database/
cp -r DATA/* ../media/bulk/
cd ../citadel
python manage.py migrate
python manage.py createsuperuser (Create a super user by following the instructions)
python manage.py crontab add
python manage.py collectstatic --noinput
deactivate
```
### Running the Web-App


You can run the code using the command:

```
cd citadel
source venv/bin/activate
cd citadel
python manage.py runserver
``` 

Thereafter, go to the home page at `localhost:8000`

For admin page go to `localhost:8000/admin/`


## Built With

* [Python 3.6](http://www.python.org/) - Python is a programming language that lets you work quickly and integrate systems more effectively.
* [Django 1.11.1](https://www.djangoproject.com/) - The web framework for perfectionists with deadlines.


## How to approve and disapprove requests?
Go to ``/books/approve`` and accept or reject or rename each request

PS: You must be logged in to do that ;)  

## Tracking: 

Tracking and Page hits are currently implemented in two ways:

1. Google Analytics - Currently, Google analytics is operational for **study.devclub.iitd.ac.in/**


## API

```
* /books/api/structure/ : would return the whole directory structure
```



						
