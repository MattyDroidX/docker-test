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