![Django Guide and Cheat sheet](https://raw.githubusercontent.com/graphenessl/django-guide/master/images/python-django.png "Django guide and Cheat sheet")

# Django guide and Cheet sheet
A guide to setting up Django, together with some basic cheat sheet commands

### Installation for Python 2.7
```python
pip install Django==1.11.9
```

---
### Start a project
```python
django-admin startproject project-name
```

---
### Generate migrations (if any)
```python
python manage.py showmigrations
```
```python
python manage.py makemigrations
```
```python
python manage.py migrate
```

---
### Create an application in the project
```python
python manage.py startapp application-name
```

Please note that a single `project` can have multiple `applications` inside it
Do not forget to include the new project in `settings.py`:

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'application-name'
]
```

---
### Collect static files (if any)
```python
python manage.py collectstatic
```

---
### Edit ``settings.py``
```python
vim project-name/settings.py
```

These are the settings of the entire **`project`** not the **`applications`**!

---
### Create a superuser
```python
python manage.py createsuperuser
```

The command will ask for **username**, **password** and **email** to be provided
If you have Django admin module enabled, this user will be able to login in the panel

---
### Run server
```python
python manage.py runserver 0.0.0.0:8000
```
---
### Models now showing up in Django admin
All models, which **you would like to be shown** in the Django admin, must be **manually specified** in the **`admin.py`** file inside your application directory. Below is an example with a model named **`Product`**

##### Define your model in ``models.py``
```python
class Product(models.Model):

    # Name of the product
    name                = models.CharField(max_length=128, default=None, blank=True, null=True)

    # Description of the product
    description         = models.TextField(max_length=8096, default=None, blank=True, null=True)

    # Date when the product is created
    date_posted         = models.DateTimeField(default=datetime.now)

    # Return name: otherwise it is not shown in the Django Admin
    def __unicode__(self):
        return self.content
```

##### Add to ``admin.py``
```python
# REQUIRED: All custom models which need to be shown in Django admin, must be manually INCLUDED here:
from .models import Product

# REQUIRED: All custom models which need to be shown in Django admin, must be manually also REGISTERED here:
admin.site.register(Product)
```
