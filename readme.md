# demo-js-nginx-docker-k8s
This is demo page of js on Nginx on Docker and k8s. 
+ js demo page.
  + Used [particles.js](https://github.com/VincentGarreau/particles.js/).
+ Dockerfile of Nginx + demo page. 
+ The manifest files for k8s Service and Deploymnet using the container image built from this repository.
+ CI is using Github Actions.
+ CD is GitOps with ArgoCD, which syncs with CI in this repository and uses a separate repository below.
  + https://github.com/tbuchi888/argocd-sample-repo.git
　
## docker build/push Commands for mac or linux
```
cd demo-js-nginx/
docker build -t takuyak/nginx-sample-bl:v1 ./
docker run -d --name demo -p 80:80 takuyak/nginx-sample-bl:v1
docker stop demo
docker rm demo
docker login
docker push takuyak/nginx-sample-bl:v1
```

## deploy to k8s
```
# edit /k8s/bl.yml and changed tag
kubectl -f /k8s/bl.yml
kubectl get all
```
