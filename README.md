<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create Kubernetes Manifests

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks3)

**Author:** Abdulrahman Abdulkadir  
**Email:** abdabdulkadir62@gmail.com

---

## Create Kubernetes Manifests

![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-compute-eks3_b01876555)

---

## Introducing Today's Project!

In this project, I will create Kubernetes manifests because they define the desired state and configuration of my backend application’s resources, allowing Kubernetes to deploy, manage, and scale them consistently.


### Tools and concepts

I used Amazon EKS, eksctl, kubectl, Docker, and Amazon ECR to build, store, and deploy my backend application on a managed Kubernetes cluster. Key concepts include using manifests to declaratively define deployments and services, containerizing applications for consistent environments, and leveraging Kubernetes orchestration for scalability, reliability, and automated management.


### Project reflection

I did this project today to gain practical experience deploying a backend application using Kubernetes on AWS and to deepen my understanding of container orchestration and cloud services. This project met my goals because I successfully built, pushed, and deployed the backend, and verified it was running smoothly on the EKS cluster.


This project took me approximately 1 hour and 30 minutes. The most challenging part was configuring the AWS permissions and ensuring the EKS cluster and ECR were properly set up for smooth deployment. My favourite part was seeing the backend pods successfully running and being able to access the application through the Kubernetes service.


---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. Steps I took to do this included provisioning an EC2 instance, installing eksctl and AWS CLI, configuring AWS credentials, and running eksctl commands to create the EKS cluster with the desired settings.


### Backend code

I retrieved the backend that I plan to deploy by installing Git on my EC2 instance and cloning the application’s repository directly from GitHub. Backend is the core part of my application responsible for handling business logic, processing requests, interacting with databases, and sending appropriate responses to the client. By cloning it from the repository, I ensured that I obtained the exact version of the source code required for this deployment, along with all necessary configuration files. This process also keeps the code under version control, allowing for easy updates, collaboration, and rollback if issues arise during deployment.


### Container image

Once I cloned the backend code, I built a container image because it bundles the application with all its dependencies into a portable unit that can run reliably in any environment. I used Docker to build the image from a Dockerfile, which specifies the base image, required packages, application files, and startup commands.


I also pushed the container image to a container registry, because Kubernetes needs a reliable and accessible location to pull the image from during deployment. To push the image to ECR, I authenticated Docker to my Amazon ECR registry, tagged the image with the repository URI, and used the docker push command to upload it securely.


---

## Manifest files

Kubernetes manifests are YAML or JSON files that define the desired configuration and state of Kubernetes resources, such as deployments, services, and volumes. Manifests are helpful because they make deployments repeatable, version-controlled, and easy to update or roll back, ensuring consistent application management across environments.


A Kubernetes deployment manages the creation, scaling, and rolling updates of pods to ensure the desired number of application instances are always running. The container image URL in my Deployment manifest tells Kubernetes exactly which image to pull and run for the backend application.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-compute-eks3_b01876554)

---

## Service Manifest

A Kubernetes Service exposes a set of pods as a single network endpoint, allowing stable access even if the pods are replaced or rescheduled. You need a Service manifest to define how traffic should be routed to these pods, which ports to use, and whether the service should be accessible internally within the cluster or externally to users.


My Service manifest sets up a NodePort service that selects pods labeled with `app: nextwork-flask-backend` and routes traffic from port 8080 on the service to port 8080 on the pods. It also assigns a port on each cluster node, allowing external access to the backend application.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-compute-eks3_b01876555)

---

## Deployment Manifest

Annotating the Deployment manifest helped me understand how to add meaningful metadata to my application resources because it allows me to track versions, add deployment notes, and integrate with monitoring or automation tools, making management and troubleshooting much easier.


A notable line in the Deployment manifest is the number of replicas, which means how many identical instances of a pod Kubernetes should run to ensure availability and load distribution. Pods are relevant to this because they are the smallest deployable units in Kubernetes, each containing one or more containers that run the backend application.


One part of the Deployment manifest I still want to know more about is the strategy section because it controls how updates are rolled out to pods, and understanding this better would help me manage deployments with zero downtime and handle rollbacks effectively.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-compute-eks3_6aae73e71)

---

---
