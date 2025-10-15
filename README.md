# Deploy an App with Docker

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eb)

**Author:** Łukasz Brodziak  
**Email:** lukasz.brodziak@gmail.com

---

![Image](http://learn.nextwork.org/surprised_maroon_fierce_chinese_gooseberry/uploads/aws-compute-eb_c4df13c84)

---

## Introducing Today's Project!

### What is Docker?

Docker is a tool that helps to create and run images of our app along with whole runtime environment.

### One thing I didn't expect...

One thing I didn't expect in this project was how quick it was to deploy the app using Elastic Beanstalk

### This project took me...

This project took me approximately 60 minutes. It was most rewarding to see the application up and running on the server.

---

## Understanding Containers and Docker

### Containers

Containers are packages that contain a fully functional app along with a runtime environment with all needed dependencies. They are useful because they provide everyone with the same environment which ensures that the application will run properly for every user.

A container image is a blueprint or template for making containers. It tells Docker exactly what to put inside each container - things like your app’s code, the libraries it needs, and any other required files.

### Docker

Docker is a tool that helps to build, deploy and manage containers. Docker Desktop is basically a GUI for docker.

Docker daemon is the engine that actually 🪄 does the thing 🪄 when you run Docker commands e.g. create a container.
In more technical terms, the Docker daemon is a background process that manages the Docker containers on your computer. It takes commands from the Docker client (i.e. commands you type into the terminal, or clicks you make through the Docker Desktop) and does the heavy lifting of building, running, and distributing your containers.

---

## Running an Nginx Image

Nginx (pronounced “engine-x”) is a web server, which is a program you use to run websites and web apps. If you want people to visit your site, you're going to need a web server to deliver your website's files to their browsers!

The command I ran to start a new container was docker run -d -p 80:80 nginx


![Image](http://learn.nextwork.org/surprised_maroon_fierce_chinese_gooseberry/uploads/aws-compute-eb_6245f5bb10)

---

## Creating a Custom Image

The Dockerfile is a blueprint for creating the docker image. Dockerfile contains information on things like base image we want to use for our custom image (e.g. particular Linux distro or programming language like Python) along with commands that should be run when the container is running. 

My Dockerfile tells Docker three things. First thing is that docker should use nginx image as a base. Second line copies a file called index.html to nginx folder. In the third one we are exposing port 80 so we can connect to our container when it is runing.

The command I used to build a custom image with my Dockerfile was docker build -t my-webb-app .  The '.' at the end of the command means that docker should use the Dockerfile from current directory.

![Image](http://learn.nextwork.org/surprised_maroon_fierce_chinese_gooseberry/uploads/aws-compute-eb_4c741d1913)

---

## Running My Custom Image

There was an error when I ran my custom image because there woas already an nginx image running and it occupied port 80. I resolved this by stopping the previoous image.

In this example, the container image is the blueprint that tells Docker the application code, dependencies, libraries etc that should go into a container. The container is the actual software that's created from this image and running the web server displaying your index.html

![Image](http://learn.nextwork.org/surprised_maroon_fierce_chinese_gooseberry/uploads/aws-compute-eb_74b5c3d619)

---

## Elastic Beanstalk

AWS Elastic Beanstalk is a service that makes it easy to deploy cloud applications without worrying about the underlying infrastructure. You simply upload your code and Elastic Beanstalk handles everything needed to get it running, like setting up servers and managing scaling. This lets you focus on your application code without having to spend too much time on managing cloud infrastructure.

In more technical terms, Elastic Beanstalk handles things like:
Capacity provisioning
Load balancing
Auto-scaling
Application health monitoring



Deploying my custom image with Elastic Beanstalk took me about 10 minutes

![Image](http://learn.nextwork.org/surprised_maroon_fierce_chinese_gooseberry/uploads/aws-compute-eb_26d5573b23)

---

## Deploying App Updates

To learn how to deploy app updates with Elastic Beanstalk, I updated my app by addin an image to website. I verfied those changes by opening the file locally.

My app updates didn't show up in my live environment immediately because they needed to be deployed. To deploy my changes, I only had to create zip archive with new version of the html file and the Dockerfile and upload it to beanstalk.

![Image](http://learn.nextwork.org/surprised_maroon_fierce_chinese_gooseberry/uploads/aws-compute-eb_5b7034684)

---

---
