# demo_cookiecutter_django

1. Install cookiecutter-django and requirements:
```
$ pip install cookiecutter
$ cookiecutter https://github.com/cookiecutter/cookiecutter-django
$ cd <what you have entered as the project_slug at setup stage>
>>> Rename psycopg2 package in requirements/local.txt and requirements/production.txt to psycopg2-binary
$ pip install -r requirements/local.txt
$ git init # A git repo is required for pre-commit to install
$ pre-commit install
```
2. Create a new PostgreSQL database:
> $ createdb --username=postgres <project_slug>
3. Set the environment variables for your database:
```
$ export DATABASE_URL=postgres://postgres:<password>@127.0.0.1:5432/<DB name given to createdb>
# Optional: set broker URL if using Celery
$ export CELERY_BROKER_URL=redis://localhost:6379/0
```
4. Apply migrations:
$ python manage.py makemigrations
$ python manage.py migrate