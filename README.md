# django-docker-template
** All python command must be executed in django_web container **

## Setup

### Config
```commandline
cp .env.example .env
```
Let's update your .env file!

### Start new django project
```commandline
docker-compose up -d
docker exec -it django_web bash
django-admin startproject projectname .
```

### Update Postgres config
```python
# projectname/settings.py
from decouple import config, Csv

DEBUG = config('APP_DEBUG', default=False, cast=bool)

ALLOWED_HOSTS = config('ALLOWED_HOSTS', default='', cast=Csv())

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': config('DB_DATABASE', default='django'),
        'USER': config('DB_USER', default='django'),
        'PASSWORD': config('DB_PASSWORD', default='secret'),
        'HOST': config('DB_HOST', default='db'),
        'PORT': config('DB_PORT', default=5432),
        'TEST': {
            'NAME': config('DB_DATABASE_TEST', default='django_test'),
            'USER': config('DB_USER_TEST', default='django_test'),
            'PASSWORD': config('DB_PASSWORD_TEST', default='secret'),
            'HOST': config('DB_HOST_TEST', default='db_test'),
            'PORT': config('DB_PORT_TEST', default=5432),
        },
    }
}
```
