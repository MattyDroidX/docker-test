## 🚀 Getting started

- Install [Python 3.8.3](https://www.python.org/downloads/release/python-383/).
- Install [PosgreSQL Client](https://pkgs.alpinelinux.org/package/v3.3/main/x86/postgresql-client).
- Install Dependencies:

  - gcc
  - libc-dev
  - linux-headers
  - postgresql-dev
  - musl-dev
  - zlib , zlib-dev

- Update pip

```bash
$ pip install --upgrade pip
```

- Install Python required libraries from requeriments.txt

```bash
$ pip install -r requeriments.txt
```

## Migrations

This application works in communication with a PostgreSQL database, so it's necessary to run migrations from Django.

```bash
#Create migrations
python manage.py makemigrations
python manage.py flush --no-input
python manage.py migrate
#Load dummy data
python manage.py loaddata initial_data.json
```

## ▶️ Launching the project

```bash
$ python manage.py runserver 0.0.0.0:8001
```

##Metodologia de resolucion

generamos archivo Dockerfile con los siguientes comandos

FROM python:3.8-alpine
RUN apk --update add gcc\
 libc-dev\
 linux-headers \
 postgresql-dev \
 musl-dev \
 zlib\
 zlib-dev
RUN mkdir app
WORKDIR /app
RUN pip3 install --upgrade pip
COPY ./requirements.txt /app/requirements.txt
RUN pip3 install -r /app/requirements.txt
COPY . /app
RUN chmod +x /app/entrypoint.sh
ENTRYPOINT ["/app/entrypoint.sh"]

Mantenemos y utilizamos archivos del requirements.txt

creamos una red con un volume con:

docker create volume myNetwork

Luego corremos la base de datos con el siguiente comando:

docker run --name backend-postgresql -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -d -p 5432:5432 --network mi_red -v db_postgres:/var/lib/postgresql/data postgres:14.4-alpine

Generamos un Build:

docker build -t django.app:latest .

y levantamos el contenedor de la siguiente manera
