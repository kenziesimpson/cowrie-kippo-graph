FROM python:3.7-alpine
RUN pip install mysql-python

FROM cowrie/cowrie
USER root
RUN apt update && apt install -y \
  libmariadb-dev-compat \
  && rm -rf /var/lib/apt/lists/*
USER cowrie