# learn-react
Learn React (Official Site)

## create a react app

npx create-react-app my-app

## Dockerize it

### Create a Dockerfile

my-app/Dockerfile

### Docker Build

docker build -t samplereactapp .

### Docker Run

docker run --name reactapp -d -p 3001:3000 samplereactapp
