# spring-boot-hello-world
This is a very simple Spring Boot Application which works well for testing CI solutions.
The applcation can be deployed into a Docker image which can then be run just as a container or apart of a Kubernetes cluster.

- It will be useful to first have [Docker Hub Account](https://hub.docker.com/signup) so that your images can be accessable on the interent
- You will need the following configured in your development environment to be able to build this applciation:
    - Java
    - Maven
    - Docker
- Make sure that the application has been built so that there is a fat JAR to copy into the Docker image:
    ```bash
    mvn clean package
    ```
- We can build the Docker image using this command replacing **bobcrutchley** with whatever your Docker Hub username is:
    ```bash
    docker build -t bobcrutchley/spring-boot-hello-world:latest
    ```
- Pushing your new Image to Docker Hub will make it accessable from anywhere:
    ```bash
    docker login
    docker push bobcrutchley/spring-boot-hello-world:latest
    ```
#### Running with Docker
- The image can also be run locally:
    ```bash
    docker run -d -p 8080:8080 --name spring-boot-hello-world --rm bobcrutchley/spring-boot-hello-world:latest
    ```
#### Running with Kubernetes
You will need the gcloud SDK installed and a free trial or subscription to Google Cloud Platform to be able to run these commands.
- Make sure that you are logged in to the GCloud SDK
    ```bash
    gcloud auth login
    ```
- Install the kubectl component, this will allow us to communicate with the Kubernetes cluster
    ```bash
    gcloud components install kubectl
    ```
- Create a new cluster
    ```bash
    gcloud container clusters create spring-boot-hello-world
    ```
- The Deployment and Service for the application can be made by running this command fromt the project root:
    ```bash
    kubectl create -f kubernetes 
    ```
