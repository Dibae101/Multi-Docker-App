
## Docker Commands

In the project directory, you can run:

TO RUN MONGO DB IMAGE:
### `docker run --name mongodb --rm -d -p 27017:27017 mongo`

BACKEND DOCKERFILE
### `docker build -t goals_node .`

### `docker run --name goals_backend --rm -p 80:80 goals_node`

