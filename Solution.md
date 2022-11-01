## Here will present the solution

#### Create a cluster with 3 nodes
$ gcloud container clusters create bootcamp \
  --machine-type e2-small \
  --num-nodes 3 \
  --scopes "https://www.googleapis.com/auth/projecthosting,storage-rw"
  
 #### Create a deployment
  $ kubectl create -f deployments/auth.yaml
  $ kubectl create -f services/auth.yaml
  
$ kubectl create -f deployments/hello.yaml
     kubectl create -f services/hello.yaml
     
$ kubectl create secret generic tls-certs --from-file tls/
   kubectl create configmap nginx-frontend-conf --from-file=nginx/frontend.conf
   kubectl create -f deployments/frontend.yaml
   kubectl create -f services/frontend.yaml
  
 --get reponse from the frontend services
$ curl -ks https://<EXTERNAL-IP>
  
 #### Scale a deployment
  
  --Kubernetes will automatically update the associated ReplicaSet and start new Pods to make the total number of Pods equal 5.
 $ kubectl scale deployment hello --replicas=5
  
 -- verify that there are now 5 pods
 $ kubectl get pods | grep hello- | wc -l
  
  #### Rolling update
  
  -- Trggir rolling update create a new deployment with hello image: 2.0.0
  
$ kubectl edit deployment hello
...
containers:
  image: kelseyhightower/hello:2.0.0
  ...
  
---Once we save out of the editor, the updated deployment will be saved to our cluster and Kubernetes will begin a rolling update.
  
$ kubectl rollout status deployment/hello ## check the statue of the rollout
  
### Canary deployments
  $kubectl create -f deployments/hello-canary.yaml
  
### Blue-green deployments
  $kubectl apply -f services/hello-blue.yaml
  
  ---The green deployment updates the version label and the image path.
  kubectl create -f deployments/hello-green.yaml
  
  #verify that the current version of 1.0.0 is still being used
  $ curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`/version 
  
  #verify that the new version is always being used:
  $kubectl apply -f services/hello-green.yaml
  
  #Rolling back if necessary:
  $kubectl apply -f services/hello-blue.yaml
