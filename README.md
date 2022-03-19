# Docker Commands
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

## WORKING WITH NETWORK

CREATING A NETWORK
### `docker network ls`
### `docker network create goals-network`

RUNNING MONGODB WITH THE NETWORK
### `docker run --name mongodb --rm -d --network goals-network mongo`

RUNNING BACKEND WITH THE NETWORK (build the image again)
### `docker build -t goals_node .`
### `docker run --name goals_backend --rm -d --network goals-network goals_node`

IMPORTANT: FRONTEND IS PROVISIONED BY WEB BROWSERS, SO RUNNING IT ONTO AN NETWORK DOESN'T SERVER THE APPLICATION. (build the image again)
### `docker build -t goals_react .`
### `docker run --name goals_frontend --rm -d -p 3000:3000 -it goals_react`

THE NODE APPLICATION IS PROVISIONED WITH MONGODB BUT STILL IT NEEDS TO COMMUNICATE WITH REACT APP ON PORT 80.
### `docker run --name goals_backend --rm -d -p 80:80 --network goals-network goals_node`

## WORKING WITH PERSISTENT VOLUME
data : HOST
/data/db: Container registry 
### `docker run --name mongodb --rm -d -v data:/data/db --network goals-network mongo`

BIND MOUNTS FOR BACKEND
### `docker run --name goals_backend -v /home/batman/Downloads/multi-01-starting-setup/backend:/app -v /app/node_modules -p 80:80 --rm -d --network goals-network goals_node`

CHECK THE LOGS
### `docker logs goals_backend`

BIND MOUNTS FOR FRONTEND

### `docker run -v /home/batman/Downloads/multi-01-starting-setup/frontend/src:/app/src --name goals_frontend --rm -d -p 3000:3000 -it goals_react`


