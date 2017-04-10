#LMNOP

## Live Music Notes, Opinions, Photographs

Assumes postgres installed and running.

Create Procfile

pip install whitenoise, gunicorn, dj-database-url, update requirements.txt

Renamed the upper LMNOPsite directory to LMNOPproject to avoid ambiguity

Replace various references to lmn with LMNOPproject.lmn   

## Python version

create runtime.txt file with python version in

Heroku expects to run things from the root dir of project. We've been running things from the LMNOPsite directory, so have to adjust where things are relative to the root.

### config vars, set in dashboard

POSTGRES_LMNOP_USER_PASSWORD= whatever your password is

Postgres database seems to be created for you. If not `heroku addons:create heroku-postgresql:dev`

Make migrations

``` heroku run python LMNOPproject/manage.py migrate ```  

OR

```heroku run bash```

then

```
cd LMNOPproject
python manage.py migrate
```

### Create superuser

``` heroku run python LMNOPproject/manage.py createsuperuser ```  



```heroku run bash```

then

```
cd LMNOPproject
python manage.py createsuperuser
```



### Collect static files

Add whitenoise, make edits to settings.py as described in heroku docs.

Disabling collect static and deploying in the current configuration seems to work (??) Must read up more on collectstatic. Possibly whitenoise looks for static files in the same place as manage.py runserver (?)

```heroku config:set DISABLE_COLLECTSTATIC=1```

### Create heroku app

```heroku create```

### run locally

```heroku local web```

App at 127.0.0.0:5000  (not :8000)

### deploy

```git push heroku master```


### TODO

DEBUG = False
Change secret key
