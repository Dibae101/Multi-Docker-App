
## Docker Commands

In the project directory, you can run:

TO RUN MONGO DB IMAGE:
### `docker run --name mongodb --rm -d -p 27017:27017 mongo`

BACKEND DOCKERFILE

### `cd backend`

### `docker build -t goals_node .`
### `docker run --name goals_backend --rm -p 80:80 goals_node`

FRONTEND DOCKERFILE
### `cd frontend`
### `docker build -t goals_react .`

### `docker run --name goals_frontend --rm -d -it 3000:3000 goals_react`

LIST CONTAINERS
### `docker ps`

LIST RUNNING CONTAINERS
### `docker ps -a`

LIST IMAGES

### `docker images`






