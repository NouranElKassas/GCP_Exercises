Make sure the following APIs are enabled in Cloud Console:

    Kubernetes Engine API
    Google Container Registry API

On the Navigation menu (Navigation menu), click APIs & services.

Scroll down and confirm that your APIs are enabled.

If an API is missing, click ENABLE APIS AND SERVICES at the top, search for the API by name, and enable it for your project.

go to google cloud shell

set compute engine to be in us-centeral1-a
```gcloud config set compute/zone us-central1-a```

clone a repo https://github.com/googlecodelabs/orchestrate-with-kubernetes.git
```git clone https://github.com/googlecodelabs/orchestrate-with-kubernetes.git```

go to orchestrate-with-kubernetes
```cd orchestrate-with-kubernetes/kubernetes```

create a container cluster
```gcloud container clusters create bootcamp --num-nodes 5 --scopes "https://www.googleapis.com/auth/projecthosting,storage-rw"```

Explain Deployment
```kubectl explain deployment``` or ```kubectl explain deployment --recursive```

Explain deployment metadata
```kubectl explain deployment.metadata.name```

Read a file  deployments/auth.yaml
```cat deployments/auth.yaml```

create a kubectl deploymet
```kubectl create -f deployments/auth.yaml```

see kubectl deployments
```kubectl get deployments```

get replicas of each deployment
```kubectl get replicasets```

create service authuntication
```kubectl create -f services/auth.yaml```

configure ngnix-frontend
```kubectl create configmap nginx-frontend-conf --from-file=nginx/frontend.conf```

create secret generic tls-certs
```kubectl create secret generic tls-certs --from-file tls/```

create deployments/frontend.yaml
```kubectl create -f deployments/frontend.yaml```

create -f services/frontend.yaml
```kubectl create -f services/frontend.yaml```

show frontend services in kubectl
```kubectl get services frontend```

test the service
``` curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"` ```

Explain deployment.spec.replicas
```kubectl explain deployment.spec.replicas```

Increase the hello deployment to be replicated 5 times
```kubectl scale deployment hello --replicas=5```

get pods contains hello
```kubectl get pods | grep hello- | wc -l```

Increase the hello deployment to be replicated 3 times
```kubectl scale deployment hello --replicas=3```

get pods contains hello
```kubectl get pods | grep hello- | wc -l```

update thedeployment from 1.0.0 to become 2.0.0
```kubectl edit deployment hello``` or ```KUBE_EDITOR="nano" kubectl edit deployment hello```

see the replicas
```kubectl get replicaset```

rollout the deployment history
```kubectl rollout history deployment/hello```

rollout the deployment pause
```kubectl rollout pause deployment/hello```

get all the pods 
```kubectl get pods -o jsonpath --template='{range .items[*]}{.metadata.name}{"\t"}{"\t"}{.spec.containers[0].image}{"\n"}{end}' ```

rollout the deployment reusme
```kubectl rollout resume deployment/hello```

rollout the deploymwent status
```kubectl rollout status deployment/hello```

rollout the deployment undo 
```kubectl rollout undo deployment/hello```

Create kubectl deployments
```kubectl create -f deployments/hello-canary.yaml```
