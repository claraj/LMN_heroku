## LMNOP

Assumes postgres installed and running.

### Create Procfile

Put command to run wsgi.py in it

### Add dependencies

pip install whitenoise, gunicorn, dj-database-url, update requirements.txt

(note updated psycopg2)

### renaming

Renamed the upper LMNOPsite directory to LMNOPproject to avoid ambiguity

Replace various references to lmn with LMNOPproject.lmn   

### Python version

create runtime.txt file with python version in

Heroku expects to run things from the root dir of project. We've been running things from the LMNOPsite directory, so have to adjust where things are relative to the root.

### config vars, set in dashboard

POSTGRES_LMNOP_USER_PASSWORD= whatever your password is

Postgres database seems to be created for you. If not `heroku addons:create heroku-postgresql:dev`

Make migrations

``` heroku run python LMNOPproject/manage.py migrate ```

OR

``` heroku run bash ```

then

```
cd LMNOPproject
python manage.py migrate
```

### Create superuser

``` heroku run python LMNOPproject/manage.py createsuperuser ```  

OR

```heroku run bash```

then

```
cd LMNOPproject
python manage.py createsuperuser
```

### Running manage.py locally

Add these lines to settings.py

```

import sys
sys.path.append('..')  ## This is needed to be able to run python manage.py

```

### Collect static files

Add whitenoise, make edits to settings.py as described in heroku docs.

https://devcenter.heroku.com/articles/django-app-configuration#migrating-an-existing-django-project

Disabling collect static and deploying in the current configuration seems to work (??) Must read up more on collectstatic. Possibly whitenoise looks for static files in the same place as manage.py runserver (?)

```heroku config:set DISABLE_COLLECTSTATIC=1```

### Create heroku app

```heroku create```

### run locally

```heroku local web```

App at 127.0.0.0:5000  (not :8000)

(Windows users: this won't work because gunicorn doesn't work on Windows. Run your app as before,

```
cd LMNOPproject
python manage.py runserver

```

### deploy

```git push heroku master```


### TODO

Change DEBUG = False in settings.py
Change secret key
