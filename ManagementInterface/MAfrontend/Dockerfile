
FROM python:latest
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install libsasl2-dev python3-dev libldap2-dev libssl-dev -y
RUN groupadd -r user

RUN useradd -r -g user user
WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt
COPY . .

ARG DJANGO_SUPERUSER_USERNAME
ARG DJANGO_SUPERUSER_PASSWORD
ARG DJANGO_SUPERUSER_EMAIL

RUN python3 manage.py makemigrations sbpmfrontend
RUN python3 manage.py migrate
RUN python manage.py createsuperuser --noinput
RUN chown -R user:user .
USER user
