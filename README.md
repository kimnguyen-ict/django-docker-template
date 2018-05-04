# django-docker-template

## Setup

### Config
```
# Copy .env file
cp .env.example .env

# Let's update your .env
```

### Start new django project
```
docker-compose up -d
docker exec -it django_web bash
django-admin startproject projectname .
```
