# Docker Multi-container App using MongoDB, NodeJS, React

## Without Docker Compose
### The initial commit shows a working setup for Docker Multi-container apps.
### Execute the following commands to test it locally. P.S. You should have docker installed on your machine.

#### Create a network
`
docker network create goals-net
`

#### MongoDB
##### Step 1: Pull abd Build a MongoDB image
`
docker pull mongo
`

`
docker build -t mongodb .
`
##### Step 2: Run MongoDB image
`
docker run --rm --network -e MONGO_INITDB_ROOT_USERNAME=<username> -e MONGO_INITDB_ROOT_PASSWORD=<password> goals-net mongodb
`

#### NodeJS Backend App
##### Step 1: Build the backend app
`
docker build -t goals-node-backend .
`
##### Step 2: Run the NodeJS App
`
docker run -p 80:80 --rm --name goals-backend -e MONGODB_USERNAME=<username> MONGODB_PASSWORD=<password> --network goals-net goals-node-backend
`

#### React Frontend App
##### Step 1: Build the frontend app
`
docker build -t goals-react-frontend .
`
##### Step 2: Run the React App
`
docker run -p 3000:3000 --rm --name goals-frontend goals-react-frontend
`


