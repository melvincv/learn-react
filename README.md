# learn-react
Learn React (Official Site)
https://reactjs.org/tutorial/tutorial.html

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

## Let's Encrypt SSL

https://cert-manager.io/docs/tutorials/acme/nginx-ingress/

1. Install cert-manager

https://cert-manager.io/docs/installation/#default-static-install

2. Enter a valid email ID in letsencrypt.yml

3. Apply letsencrypt.yml

k apply -f letsencrypt.yml

4. The let's encrypt HTTP validation fails due to incorrect DNS (Local PC). But it should work on the Cloud.

```
$ kubectl get cert -n myreactapp
NAME                READY   SECRET              AGE
reactapp-tls-cert   False   reactapp-tls-cert   6m13s

$ k describe cert -n myreactapp

Events:
  Type    Reason     Age    From                                       Message
  ----    ------     ----   ----                                       -------
  Normal  Issuing    7m19s  cert-manager-certificates-trigger          Issuing certificate as Secret does not exist
  Normal  Generated  7m19s  cert-manager-certificates-key-manager      Stored new private key in temporary Secret resource "reactapp-tls-cert-st7nl"
  Normal  Requested  7m19s  cert-manager-certificates-request-manager  Created new CertificateRequest resource "reactapp-tls-cert-qcgbk"

$ k logs cert-manager-b4d6fd99b-25pt2 -n cert-manager

E0419 10:46:43.474919       1 sync.go:186] cert-manager/challenges "msg"="propagation check failed" "error"="failed to perform self check GET request 'http://reactapp.melvincv.site/.well-known/acme-challenge/h1iOzNKfKytjosx7Iu5-CLQ9o7bfYr10K2MFDGMqGZ4': Get \"http://reactapp.melvincv.site/.well-known/acme-challenge/h1iOzNKfKytjosx7Iu5-CLQ9o7bfYr10K2MFDGMqGZ4\": dial tcp: lookup reactapp.melvincv.site on 10.96.0.10:53: no such host" "dnsName"="reactapp.melvincv.site" "resource_kind"="Challenge" "resource_name"="reactapp-tls-cert-qcgbk-3508114203-3079109504" "resource_namespace"="myreactapp" "resource_version"="v1" "type"="HTTP-01"
```