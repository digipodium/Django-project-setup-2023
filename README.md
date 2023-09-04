# Setting up a simple django setup 

`Team Digipodium` presents

## clearing some Jargon
- `Django` is a web framework that helps you create websites using Python.
- `Static files` are files that do not change, such as images, CSS, and JavaScript. 
- `Templates` are files that contain HTML code and Django tags that can display dynamic data from the server.

To set up a Django project with static and templates folders, you need to follow these steps:

1. Install Python and Django on your computer. You can download Python(miniconda) from [here](^https://docs.conda.io/projects/miniconda/en/latest/^) and Django `pip install django`. Follow the instructions to install them properly.
2. Create a folder for your project, such as `myproject`, and open it in your code editor or terminal. You can use any code editor you like, such as Visual Studio Code, PyCharm, etc.
3. Create a virtual environment for your project using the `virtualenv` command. A virtual environment is a way to isolate your project's dependencies from other projects. To create a virtual environment, type `virtualenv env` in your terminal and press Enter. This will create a folder called `env` inside your project folder.
4. Activate the virtual environment using the `activate` command. To activate the virtual environment, type `source env/bin/activate` in your terminal and press Enter. This will change your prompt to `(env)`.
5. Install Django in your virtual environment using the `pip` command. Pip is a tool that helps you install Python packages. To install Django, type `pip install django` in your terminal and press Enter. This will download and install Django in your virtual environment.
6. Create a new Django project using the `django-admin` command. Django-admin is a tool that helps you create and manage Django projects. To create a new Django project, type `django-admin startproject myproject` in your terminal and press Enter. This will create a folder called `myproject` inside your project folder, which contains some files and folders that are essential for a Django project.
7. Run the Django server using the `manage.py` command. Manage.py is a file that helps you run various commands for your Django project. To run the Django server, type `python manage.py runserver` in your terminal and press Enter. This will start the server on your local machine and show you a message like this:

```
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
April 15, 2023 - 15:04:53
Django version 4.2, using settings 'myproject.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

8. Open your web browser and go to http://127.0.0.1:8000/. You should see a page that says "The install worked successfully! Congratulations!" This means that your Django project is working correctly.
9. Create a new app for your project using the `manage.py` command. An app is a component of a Django project that contains models, views, templates, and other files related to a specific feature or functionality of your website. To create a new app, type `python manage.py startapp myapp` in your terminal and press Enter. This will create a folder called `myapp` inside your project folder, which contains some files and folders that are essential for a Django app.
10. Register your app in the settings.py file of your project. Settings.py is a file that contains various configurations for your Django project, such as installed apps, database settings, static files settings, etc. To register your app, open the settings.py file in your code editor and find the line that says `INSTALLED_APPS = [...]`. Add `'myapp'` to the list of installed apps, like this:

```python
# myproject/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp', # add this line
]
```

11. Create static and templates folders inside your app folder. Static and templates folders are where you store your static files and templates for your app respectively. To create these folders, type `mkdir myapp/static myapp/templates` in your terminal and press Enter.
12. Set static and templates directories in the settings.py file of your project. To tell Django where to look for static files and templates for your app, you need to add some lines to the settings.py file of your project, like this:

```python
# myproject/settings.py
import os # add this line

# ...

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/4.2/howto/static-files/

STATIC_URL = '/static/'
STATICFILES_DIRS = [os.path.join(BASE_DIR, 'myapp/static')] # add this line

# Templates
# https://docs.djangoproject.com/en/4.2/topics/templates/

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'myapp/templates')], # add this line
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

13. Add some static files and templates to your app folder. To test if your static files and templates are working correctly, you can add some files to your app folder, such as a CSS file, a JavaScript file, an image file, and an HTML file. For example, you can create these files in your app folder:

- `myapp/static/style.css`
- `myapp/static/script.js`
- `myapp/static/image.jpg`
- `myapp/templates/index.html`

You can write any content you want in these files, or you can use some sample content from [here](^3^), [here](^4^), [here](^5^), and [here](^6^) respectively.

To use these static files and templates in your app, you need to do two more things:

- Create a view function in the views.py file of your app. Views.py is a file that contains functions that handle requests and return responses for your app. To create a view function, open the views.py file in your code editor and add a function like this:

```python
# myapp/views.py
from django.shortcuts import render

def index(request):
    # this function renders the index.html template
    return render(request, 'index.html')
```

This function takes a request object as a parameter and returns a response object that renders the index.html template.

- Create a URL pattern in the urls.py file of your project. Urls.py is a file that contains patterns that map URLs to view functions for your project. To create a URL pattern, open the urls.py file in your code editor and add a line like this:

```python
# myproject/urls.py
from django.contrib import admin
from django.urls import path
from myapp import views # add this line

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.index), # add this line
]
```

This line tells Django to call the index view function when the user visits the root URL of your website.

That's it! You have successfully set up a Django project with static and templates folders. To see the result, restart the Django server by pressing Ctrl+C in your terminal and typing `python manage.py runserver` again. Then go to http://127.0.0.1:8000/ in your web browser and you should see something like this:

![A web page with some text, an image, and some styling](#graphic_art("A web page with some text, an image, and some styling"))

I hope you learned something useful from this tutorial. If you have any questions or feedback, please let me know. 😊

Source: Conversation with Bing, 4/9/2023
(1) Working with Django Templates & Static Files | DigitalOcean. https://www.digitalocean.com/community/tutorials/working-with-django-templates-static-files.
(2) Django Static Files and Templates | LearnDjango.com. https://learndjango.com/tutorials/django-static-files-and-templates.
(3) Complete Setup of Django Project In 13 Steps | Medium. https://medium.com/@umaraziz021/complete-step-up-of-django-project-in-13-simple-steps-17d394410c99.
(4) How to manage static files (e.g. images, JavaScript, CSS) | Django .... https://docs.djangoproject.com/en/4.2/howto/static-files/.
(5) undefined. https://docs.djangoproject.com/en/1.10/howto/static-files/.
(6) undefined. http://127.0.0.1:8000/static/.
(7) undefined. http://127.0.0.1:8000/static/base.css.
