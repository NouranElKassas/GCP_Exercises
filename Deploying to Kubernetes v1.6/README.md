# Deploying to Kubernetes v1.6  on GCP

The new goal of this lab is to get you ready for scaling and managing containers in production.

And that's where deployments come in. Deployments are a declarative way to ensure that the number of pods running is equal to the desired number of pods specified by the user.
Introduction to Deployments

Deployments abstract away the low level details of managing pods. They provide a single stable name that you can use to update an application. Behind the scenes, deployments rely on ReplicaSets to manage starting, stopping, scaling, and restarting the pods if they happen to go down for some reason. If pods need to be updated or scaled, the deployment will handle all of the details for you.

Deployments (and ReplicaSets) are powered by control loops. Control loops are a design pattern for distributed software that allows you to declaratively define your desired state and have the software implement the desired state for you based on the current state. You'll see more about how that works below.
