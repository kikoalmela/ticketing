# Microservices Ticketing App

Events ticket selling app.  
Stack:
* React SSR client, on Next framework
* Backend microservices on nodeJS, with Express.
* NATS Streaming Server for events messaging.

---
## Microservices
Docker pods orchestrated with kubernetes.  
Skaffold for build and deploy.  

From the root directory, run:

```shell
skaffold dev
```

## Client
To start the Next client:
```shell
npm run dev
```

## Testing
Developed using TDD  
Testing library: Jest

From every service directory we can run:
```shell
npm run test
```
---
## Useful local dev commands
### Trying out nats-test service
nats-test service is listening on port 4222  

* Run:  
`kubectl get pods`  
* Copy `nats-depl` pod's name

* Make kubernetes forward calls to nats-test service. Run:  
`kubectl port-forward nats-depl-name 4222:4222`

* From a terminal window, in the nats-test directory, run:  
`npm run publish`  
* In the same directory, from a new terminal window, run:  
`npm run listen`  

This will start our nats-test publisher and listener. We can start as many listener as we want.