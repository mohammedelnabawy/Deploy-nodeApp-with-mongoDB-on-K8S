# Deploy-nodeApp-with-mongoDB-on-K8S
The repository contain some steps to deploy nodejs express backend application with mongoDB database on a kubernates cluster.
## Create Docker image from Nodejs app
```
you can check the node app from: https://github.com/mohammedelnabawy/socialMedia-nodeJS-project
```
```
docker build . -t elnabawy/nodeapp
```
```
docker login
```
```
docker push elnabawy/nodeapp
```
