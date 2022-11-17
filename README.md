- https://cloudgeeks.ca

- https://blog.devstream.io/posts/devsecops-jenkins-in-k8s-with-secret-scan/

- https://github.com/GoogleContainerTools/kaniko



##### Terraform EKS
- https://github.com/quickbooks2018/terraform-aws-eks


##### GCP


### Jenkins Commands

##### k8 credentials
```k8-secrets
kubectl create secret docker-registry docker-credentials --docker-username=[userid] --docker-password=[Docker Hub access token] --docker-email=[user email address] --namespace jenkins
```


### Jenkins Service Account
```k8-secrets
kubectl create serviceaccount jenkins --namespace=jenkins
kubectl describe secret $(kubectl describe serviceaccount jenkins --namespace=jenkins | grep Token | awk '{print $2}') --namespace=jenkins
kubectl create rolebinding jenkins-admin-binding --clusterrole=admin --serviceaccount=jenkins:jenkins --namespace=jenkins
```


##### Jenkins Kaniko CI & HELM CD Pipe
```jenkins-pipe
kubectl create ns hello
kubectl create rolebinding jenkins-admin-binding --clusterrole=admin --serviceaccount=jenkins:jenkins --namespace=hello
kubectl create rolebinding jenkins-admin-binding --clusterrole=admin --serviceaccount=jenkins:default --namespace=hello
```