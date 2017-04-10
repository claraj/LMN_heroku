#LMNOP

## Live Music Notes, Opinions, Photographs

Assumes postgres installed and running.

Create Procfile

pip install whitenoise, gunicorn, dj-database-url, update requirements.txt

Replace various references to lmn with LMNOPsite.lmn   

## Python version

create runtime.txt file with python version in

Heroku expects to run things from the root dir of project. We've been running things from the LMNOPsite directory, so have to adjust where things are relative to the root.

### Collect static files

### Create heroku app

```heroku create```

### run locally

```heroku local web```

App at 127.0.0.0:5000  (not :8000)

### deploy

```git push heroku master```

### Postgres on Heroku

Create superuser

migrations
