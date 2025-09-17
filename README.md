# Hello-Docker

A simple Docker setup to run a Node.js application that prints "Hello Docker".

## Overview

This project demonstrates how to create a lightweight Docker image for a Node.js application using the `node:alpine` base image, build it, run it locally, push it to Docker Hub, and pull/run it on another machine.

## Steps

1. **Create `app.js`**  
   Create a file named `app.js` with the following code to print "Hello Docker":

   ```javascript
   console.log("Hello Docker");
   ```

2. **Create `Dockerfile`**  
   Create a `Dockerfile` with the following content:

   ```dockerfile
   FROM node:alpine
   COPY . /app
   WORKDIR /app
   CMD ["node", "app.js"]
   ```

   - `FROM node:alpine`: Uses the lightweight `node:alpine` image as the base for minimal size.
   - `COPY . /app`: Copies all files from the current directory to the `/app` directory in the container.
   - `WORKDIR /app`: Sets `/app` as the working directory for subsequent commands.
   - `CMD ["node", "app.js"]`: Runs `node app.js` when the container starts.

3. **Build the Docker Image**  
   Run the following command to build the Docker image from the `Dockerfile` in the current directory:

   ```bash
   docker build -t hello-docker .
   ```

   - `-t hello-docker`: Tags the image as `hello-docker`.
   - `.`: Specifies the current directory containing the `Dockerfile`.

4. **Run the Docker Image Locally**  
   Test the image locally by running:

   ```bash
   docker run hello-docker
   ```

   This should output `Hello Docker` to the console.

5. **Push the Image to Docker Hub**  
   Push the image to Docker Hub (replace `myusername` with your Docker Hub username):

   ```bash
   docker push myusername/hello-docker
   ```

   Ensure you are logged in to Docker Hub using `docker login` before pushing.

6. **Test on Another Machine**  
   To verify the image works on another machine, you can use a platform like [Play with Docker](https://labs.play-with-docker.com/). Follow these steps:

   - Pull the image:

     ```bash
     docker pull myusername/hello-docker
     ```

   - Run the image:

     ```bash
     docker run myusername/hello-docker
     ```

   This should output `Hello Docker`, confirming the image works on any machine with Docker installed.

## Conclusion

This setup demonstrates a simple yet effective way to package a Node.js application in a Docker container, distribute it via Docker Hub, and run it on any Docker-compatible machine.