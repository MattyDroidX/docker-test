# build the image based on python:3.8-slim-buster image
FROM python:3.8-slim-buster

# the work directory inside the container
WORKDIR /

# copy the requirements file inside the container
COPY ./requirements.txt /requirements.txt

# install the requirements using pip3
RUN pip3 install -r requirements.txt

RUN mkdir app
WORKDIR /app

# copy the project artefects into the container under the root directory
COPY . .

# the command to run once we run the container 
CMD [ "python3" "app.py" ]