# spring-boot-hello-world
This is a very simple Spring Boot Application which works well for testing CI solutions.
The application can be deployed into a Docker image which can then be run just as a container or apart of a Kubernetes cluster.
For an example of how this project can be implemented into a simple pipeline, see the [spring-boot-hello-world-ci](https://github.com/bob-crutchley/spring-boot-hello-world-ci) project.

- It will be useful to first have [Docker Hub Account](https://hub.docker.com/signup) so that your images can be accessible on the internet
- You will need to [Install Docker](docs/install_docker.md)
- We can build the Docker image using this command replacing **bobcrutchley** with whatever your Docker Hub username is:
    ```bash
    docker build -t bobcrutchley/spring-boot-hello-world:latest
    ```
- Pushing your new Image to Docker Hub will make it accessible from anywhere:
    ```bash
    docker login
    docker push bobcrutchley/spring-boot-hello-world:latest
    ```
#### Running with Docker
- The image can also be run locally:
    ```bash
    docker run -d -p 8080:8080 --name spring-boot-hello-world --rm bobcrutchley/spring-boot-hello-world:latest
    ```
#### Running with Kubernetes (Google Cloud Platform)
You will need to have the following to be able to these commands:
- A free trial or subscription to [Google Cloud Platform](https://console.cloud.google.com/freetrial)
- Have the [GCloud SDK installed](https://cloud.google.com/sdk/docs)
- Have the Kubernetes Engine API enabled (Requires GCloud SDK to be installed)
	```bash
	gcloud services enable containers.googleapis.com
	```

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
- The Deployment and Service for the application can be made by running this command from the project root:
    ```bash
    kubectl create -f kubernetes 
    ```
