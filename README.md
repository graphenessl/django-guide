![Django Guide and Cheat sheet](https://raw.githubusercontent.com/graphenessl/django-guide/master/images/python-django.png "Django guide and Cheat sheet")

# Django guide and Cheet sheet
A guide to setting up Django, together with some basic cheat sheet commands

### Installation for Python 2.7
```pip install Django==1.11.9```

---
### Start a project
```django-admin startproject project-name```

---
### Generate migrations (if any)
```python manage.py showmigrations```
```python manage.py makemigrations```
```python manage.py migrate```

---
### Create an application in the project
```python manage.py startapp applicaiton-name```

---
### Collect static files (if any)
```python manage.py collectstatic```

---
### Edit ```settings.py```
vim 

---
### Run server
```python manage.py runserver 0.0.0.0:8000```
