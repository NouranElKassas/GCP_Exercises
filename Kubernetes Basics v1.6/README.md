# Kubernetes Basics on GCP
Overview

In this lab, you learn how to:

    Provision a Kubernetes cluster using Google Kubernetes Engine.
    Deploy and manage Docker containers using kubectl.
    Split an application into microservices using Kubernetes' Deployments and Services.

You use Kubernetes Engine and its Kubernetes API to deploy, manage, and upgrade applications. You use an example application called "app" to complete the labs.

App is hosted on GitHub. It's a 12-Factor application with the following Docker images:

    Monolith: includes auth and hello services.
    Auth microservice: generates JWT tokens for authenticated users.
    Hello microservice: greets authenticated users.
    nginx: frontend to the auth and hello services.

