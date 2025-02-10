## Docker commands

Docker commands are essential for building, managing, and deploying containerized applications. Here's an explanation of some important Docker commands:

1. docker run: This command creates and starts a container based on a Docker image. It's one of the most commonly used Docker commands.

    Example: 
    ```bash
    docker run <image_name>
    ```
2. docker build: This command builds a Docker image from a Dockerfile, which contains instructions on how to assemble the image.

    Example:
    ```bash
    docker build -t <image_name> .
    ```
3. docker pull: This command pulls a Docker image from a registry, such as Docker Hub, to your local machine.

    Example:
    ```bash
    docker pull <image_name>
    ```
4. docker push: This command pushes a Docker image from your local machine to a registry.

    Example:
    ```bash
    docker push <image_name>
    ```
5. docker ps: This command lists the currently running containers.

    Example:
    ```bash
    docker ps
    ```
6. docker ps -a: This command lists all containers, including stopped ones.

    Example:
    ```bash
    docker ps -a
    ```
7. docker stop: This command stops a running container.

    Example:
    ```bash
    docker stop <container_id>
    ```
8. docker rm: This command removes one or more containers.

    Example:
    ```bash
    docker rm <container_id>
    ```
9. docker rmi: This command removes one or more Docker images.

    Example:
    ```bash
    docker rmi <image_name>
    ```
10. docker exec: This command runs a command in a running container.

    Example:
    ```bash
    docker exec -it <container_id> <command>
    ```

11. docker logs: This command displays the logs of a container.

    Example:
    ```bash
    docker logs <container_id>
    ```
12. docker-compose: This command is used to manage multi-container Docker applications. It uses a YAML file to define services, networks, and volumes for the application.

    Example:
    ```bash
    docker-compose up -d
    ```
## Missing the "docker copy" command in the previous list. Let's include that along with a couple of other important Docker commands:
1. docker copy: This command allows you to copy files or directories between a container and the local filesystem. It's useful for transferring data into or out of containers.
    Example:
    ```bash
    # Copy a file from a container to the local filesystem
    docker cp <container_id>:/path/to/container/file.txt /path/to/local/destination
        # Copy a file from the local filesystem to a container
    docker cp /path/to/local/file.txt <container_id>:/path/to/container/destination
    ```
2. docker inspect: This command provides detailed information about Docker objects such as containers, images, volumes, networks, and more. It's useful for troubleshooting and debugging Docker-related issues.
    Example:
    ```bash
    # Inspect a container
    docker inspect <container_id>
        # Inspect an image
    docker inspect <image_name>
    ```
3. docker network: This command is used to manage Docker networks, which allow containers to communicate with each other. It provides subcommands for creating, listing, inspecting, and deleting networks.
    Example:
    ```bash
    # List Docker networks
    docker network ls
        # Create a Docker network
    docker network create my_network
   # Inspect a Docker network
    docker network inspect my_network
    ```
4. docker volume: This command is used to manage Docker volumes, which provide persistent storage for containers. It provides subcommands for creating, listing, inspecting, and deleting volumes.
    Example:
    ```bash
    # List Docker volumes
    docker volume ls
    # Create a Docker volume
    docker volume create my_volume
    # Inspect a Docker volume
    docker volume inspect my_volume
    ```
5. docker-compose down: This command stops and removes containers, networks, and volumes defined in a docker-compose.yml file. It's used to clean up resources after running docker-compose up.
    Example:
    ```bash
    docker-compose down

## DockerFile Commands:
Certainly! Dockerfile commands are used to build Docker images by defining the steps needed to create a containerized application. Here's a brief explanation of each Dockerfile command:
1. FROM: Specifies the base image for the Docker image. Every Dockerfile must start with a FROM command.
    Example:
    ```Dockerfile
    FROM ubuntu:20.04
    ```
2. RUN: Executes commands during the image build process. It's commonly used for installing dependencies, running build scripts, or performing any necessary setup tasks.
    Example:
    ```Dockerfile
    RUN apt-get update && apt-get install -y \
        package1 \
        package2
    ```
3. COPY: Copies files or directories from the build context (local filesystem) into the image.
    Example:
    ```Dockerfile
    COPY . /app
    ```
4. ADD: Similar to COPY but has additional features like extracting tarballs and fetching remote URLs. It's generally recommended to use COPY unless you specifically need ADD's extra features.
    Example:
    ```Dockerfile
    ADD http://example.com/file.txt /app/
    ```
5. WORKDIR: Sets the working directory for subsequent commands in the Dockerfile.

    Example:
    ```Dockerfile
    WORKDIR /app
    ```
6. ENV: Sets environment variables in the container.
    Example:
    ```Dockerfile
    ENV NODE_ENV=production
    ```
7. EXPOSE: Informs Docker that the container listens on specific network ports at runtime. It does not actually publish the port.
    Example:
    ```Dockerfile
    EXPOSE 8080
    ```
8. CMD: Provides default command and/or arguments for executing the container. CMD can be overridden when running the container.
    Example:
    ```Dockerfile
    CMD ["node", "app.js"]
    ```
9. ENTRYPOINT: Configures the container to run as an executable. It's often used in combination with CMD to provide default arguments.
    Example:
    ```Dockerfile
    ENTRYPOINT ["node", "app.js"]
    ``
10. VOLUME: Creates a mount point and/or marks a directory as externally mounted. It's used for persistent data and stateful applications.

    Example:
    ```Dockerfile
    VOLUME /data
    ```
11. USER: Sets the user or UID to use when running the image.
    Example:
    ```Dockerfile
    USER appuser
    ```
12. LABEL: Adds metadata to an image in the form of key-value pairs.
    Example:
    ```Dockerfile
    LABEL version="1.0" \
          description="My Docker image"
    ```
Example
Certainly! Here's a Dockerfile example for building a Docker image for a Java application packaged as a `.war` file, typically used in Java web applications like those built with Spring MVC or Java EE:
```Dockerfile
# Use the official Tomcat image as the base image
FROM tomcat:9-jdk11
# Remove the default ROOT application from Tomcat
RUN rm -rf /usr/local/tomcat/webapps/ROOT
# Copy the WAR file to the Tomcat webapps directory
COPY target/my-web-app.war /usr/local/tomcat/webapps/ROOT.war
# Expose port 8080 to allow communication to/from the container
EXPOSE 8080
# Start Tomcat when the container starts
CMD ["catalina.sh", "run"]
Explanation:
- FROM: Specifies the base image for the Docker image. Here, we're using the official Tomcat image from Docker Hub, which includes Apache Tomcat with Java runtime.
- RUN: Executes a command during the image build process. In this case, we're removing the default `ROOT` application that comes with Tomcat to make room for our own application.
- COPY: Copies the `.war` file of the Java web application (typically located in the `target` directory after building the application) from the local filesystem to the Tomcat webapps directory inside the container. We're renaming it to `ROOT.war` so that it deploys as the root application in Tomcat.
- EXPOSE: Informs Docker that the container listens on port 8080 at runtime. This does not actually publish the port but documents which ports are intended to be published.
- CMD: Defines the default command to start Tomcat when the container is started. It executes `catalina.sh run`, which starts Tomcat and serves the deployed web application.
This Dockerfile sets up a Docker image that contains a Java web application packaged as a `.war` file. When the image is run as a container, it will start Apache Tomcat and deploy the web application, allowing users to access it via port 8080. This example demonstrates how to create a Dockerfile for a Java web application deployed on a Tomcat server within a Docker container.
