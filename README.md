# learn-react
Learn React (Official Site)

## create a react app

npx create-react-app my-app

## Docker

### Create a Dockerfile

my-app/Dockerfile

### Docker Build

docker build -t samplereactapp .

### Docker Run

docker run --name reactapp -d -p 80:80 samplereactapp

## Kubernetes

kubectl apply -f kubernetes/app.yaml
