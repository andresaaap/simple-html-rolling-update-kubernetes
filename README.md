# Simple index.html website deployment in Kubernetes with rolling update for zero-down time updates

The idea of this project is to show a solution for implementing a simple index.html website that can be deployed to a kubernetes and has configured a rolling update strategy to make sure that this website has zero-down time updates.

**Important for Udacity Cloud DevOps students**

This is how you can implement the rolling update in your Capstone project. You will have to adapt it and integrate it to your project
### Requirements

* Minikube: Install it you haven't
* Dockerhub: Create a Dockerhub account if you don't have one
* Docker: Install it you haven't


### Install

1. Download or clone this project

### Usage

1. Open the terminal or console in your machine
2. Change directory to the project's directory

```
cd /PATH_TO_PROJECT_DIRECTORY
```

3. Start minikube to create the kubernetes cluster

```
minikube start
```

4. Create the deployment 

```
kubectl apply -f deployment.yml
```

4. Create the service that is going to make your pods accessible 

```
kubectl apply -f service.yml
```

5. Make that you can communicate with the service resource in the cluster from your local machine

```
minikube service <NAME_OF_SERVICE_RESOURCE>
```

6. Test the website in your browser

![website image](https://github.com/andresaaap/simple-html-rolling-update-kubernetes/blob/main/img/website-image.png?raw=true)

7. Now we want to make a change in the website and execute a rolling update. We are going to start by changing the website's background color to green. Plese do this your self.

8. Build the docker image

```
docker build -t YOUR_DOCKERHUB_REPO_USERNAME/myimage .
```

9. Push the image to you docker repository


```
docker push YOUR_DOCKERHUB_REPO_USERNAME/myimage
```

10. Trigger the rolling update:

```
kubectl set image deployment/simple-html-rolling-update simple-html-container=YOUR_DOCKERHUB_REPO_USERNAME/myimage:latest
```

11. Test the website in your browser

![green website image](https://github.com/andresaaap/simple-html-rolling-update-kubernetes/blob/main/img/website-image-green.png?raw=true)



### Personalize the code for your Udacity project or other use cases

- You will need to put your image name in the deployment.yml
- You will need to set the correct ports in the deployment.yml and service.yml

### Links & Resources

* [Interactive tutorial: Performing a Rolling Update](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/)
* [Stack overflow | Kubernetes how to make Deployment to update image](https://stackoverflow.com/questions/40366192/kubernetes-how-to-make-deployment-to-update-image)
* [How images work in kubernetes](https://kubernetes.io/docs/concepts/containers/images/)
* [Command: kubectl set image](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#-em-image-em-)
* [How to configure and execute a rolling update strategy in kubernetes?](https://andresaaap.medium.com/how-to-configure-and-execute-a-rolling-update-strategy-in-kubernetes-5e662be968b)