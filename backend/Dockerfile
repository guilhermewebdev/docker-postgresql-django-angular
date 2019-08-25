# Construindo a aplicação
FROM python:latest

ENV PYTHONUNBUFFERED 1

RUN apt-get update && apt full-upgrade -y && mkdir /code
WORKDIR /code
VOLUME [ ".:/code" ]

ADD requirements.txt /code
RUN pip install --no-cache-dir -r requirements.txt

ADD . /code

# Expora aplicação
FROM httpd:latest

RUN apt-get update && apt full-upgrade -y && apt-get install libapache2-mod-wsgi-py3 -y

COPY . /usr/local/apache2/htdocs/
COPY my-httpd.conf /usr/local/apache2/conf/httpd.conf

VOLUME [ ".:/usr/local/apache2/htdocs/" ]
