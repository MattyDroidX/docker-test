#  🚀 TODO List - [Flask] - DOCKER Hands-On
#### Simple web-project to practice docker and deployment concepts
- Writing docker files
- Building images
- Running container and manage 


## ▶️ Running with Docker


```bash
# create docker volume for the database to keep your tasks everytime you run ir
$ docker volume create todolist.db

# this will build the docker image from the docker file
$docker build -t todo-list-flask:latest .

# run the container
# map port 5000 in the container to 5001 (or any other free port)
# map the docker volume you created to /app/db 
$ docker run -d -p 5001:5000 -env-file .env -v todolist.db:/app/db todo-list-flask:latest

# open the browser, go to http://0.0.0.0:5001 and here is your todo list up and running
```


```
## ▶️ Running without Docker

```bash
$ git clone git@github.com:craftech-academy/academy-devops-junio-2022-tarea-clase-2.git
$ cd academy-devops-junio-2022-tarea-clase-2/0-todo-list-flask
$ python3 -r requirements.txt
$ python3 app.py
```

