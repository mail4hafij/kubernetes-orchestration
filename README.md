# kubernetes Orchestration
The idea is to orchestrate microservices in Kubernetes. Please find the other repositories (https://github.com/mail4hafij/rabbit_event_stream, and https://github.com/mail4hafij/notification_service). Rabbit-event-stream repo, is a webserver which adds events to RabbitMQ. The Notification-service repo, is a console app which sends slack notification and sends out emails using SendGrid API. In this project, we are going to orchestrate both those microservices into Kubernetes. The example here covers, deployment to the local docker kubernetes service. So make appropriate changes when deploying to production clusters (i.e., Azure Managed Kubernetes).


# TODO
  1. Explain the figure.
  2. Explain the other github repos (rabbit_event_stream, notification_service)
  3. Explain how orchestration works?
  4. Explain all the yaml resource files.
  
 
 <img src="Application.jpg" />
