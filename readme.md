## Code

* manifests\hello-app-deployment.yaml
1. The line 21 will fetch our docker image from the ECR repo.
2. In ci/cd process we will replace the line 21 DOCKER_IMAGE with the actual ECR docker image URL. If you want you can hardcoded this line as follows.

`image: *********.dkr.ecr.us-east-1.amazonaws.com/flask-app:776ab02`
3. The deployment file will spin up the number of pods from docker image as replicas.
4. We also define the labels in the file which help kubernetes service to identify the resources.

* manifests\hello-app-service.yaml
1. this file will pick up our deployment pods and export it to the outside of the Kubernetes so larger audience can play with our app.
2. We defined Kind as service and type as load balancer which will tell kubernetes to create a load balancer service which will point to the our hello-app label deployment. 
3. Also if you remember we exported 8080 port from deployment file that we can take in this service to help service to identify on which port our app is running.

## References

1. https://towardsaws.com/build-push-docker-image-to-aws-ecr-using-github-actions-8396888a8f9e
2. https://hackernoon.com/building-a-cicd-pipeline-with-aws-k8s-docker-ansible-git-github-apache-maven-and-jenkins