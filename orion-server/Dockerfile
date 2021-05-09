FROM python:3.8.6-slim
MAINTAINER Alok Nikhil <aloknnikhil@gmail.com>

ARG sha
ARG database_host
ARG database_port
ARG database_name
ARG database_user
ARG database_password

RUN apt-get update && apt-get install -y wget unzip python3-dev default-libmysqlclient-dev gcc build-essential git

RUN git clone https://github.com/aloknnikhil/orion-server.git
WORKDIR orion-server

RUN pip3 install -r requirements.txt
RUN pip3 install gunicorn

ENV DATABASE_HOST $database_host
ENV DATABASE_PORT $database_port
ENV DATABASE_PORT $database_port
ENV DATABASE_NAME $database_name
ENV DATABASE_USER $database_user
ENV DATABASE_PASSWORD $database_password
ENV PYTHONPATH "/orion-server"

EXPOSE 80

RUN pip3 install mysqlclient

CMD make init-db && gunicorn --bind 0.0.0.0:80 -w 4 orion.server:app
