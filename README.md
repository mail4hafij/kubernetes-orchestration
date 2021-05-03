# Kubernetes Orchestration
The idea is to orchestrate multiple micro services in Kubernetes. Please find the other repositories (https://github.com/mail4hafij/rabbit_event_stream, and https://github.com/mail4hafij/notification_service). Rabbit-event-stream repo, is a webserver which adds events to RabbitMQ. The Notification-service repo, is a console app which sends slack notification and sends out emails using SendGrid API. In this project, we are going to orchestratethe microservices that are developed in those repositories. The example here covers, deployment to a local docker kubernetes service. So make appropriate changes when deploying to production clusters (i.e., Azure Managed Kubernetes).


## Changes you need to do
  1. Update the *settings.dev.json* and *settings.prod.json* files in the repo https://github.com/mail4hafij/notification_service with your SendGrid api key and your link to Slack channel.
  2. Change the storage class type in *storage-class.yaml* with your prefered storage class type.
  3. Make appropriate changes to PVCs in *rabbit_event_stream/rabbit-pvc.yaml*, *rabbit_event_stream/server-pvc.yaml* and *notification_service/notification-pvc.yaml* according to your storage needs.
  4. Build an image for the server-pod (that publishes events to rabbitMQ) and push it to your favorit image/container repository.
  5. Build an image for the notification-pod (that receives events from rabbitMQ) and push it to your favorit image/container repository.
  6. Point the server-pod image location in the *rabbit_event_stream/server-deployment.yaml* file (for now it is using my public image for rabbit_event_stream_server in dockerHub).
  7. Point the notification-pod image in the *notification_service/notificaiton-deployment.yaml* file (for now it is using my public image for notification_service_src in dockerHub). 
  
**Disclaimer:** I am using loadbalancer as the service type for *rabbit-service.yaml*, and *server-service.yaml*. But in production environment, you should avoid loadbalancer service type, rather use a reverse proxy to guide all external traffic to those services.

## Conceptual model
<img src="Application.jpg" />

### Useful commands
To get a yaml format of a service from Kubernetes
kubectl get service servicename -n <namespace> -o yaml

To get a yaml format of a service from Kubernetes to file
kubectl get service servicename -n <namespace> -o yaml > service.yaml
