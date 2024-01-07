FROM python:latest
RUN apt-get update
RUN apt-get upgrade -y
RUN groupadd -r user
RUN useradd -r -g user user
WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt

COPY . .
RUN chown -R user:user .
USER user

