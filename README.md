# Dockerizing My Portfolio Application

This project demonstrates how I containerized my personal portfolio website using **Docker** and made it accessible both locally and via Docker Hub. 

---

## 🚀 Project Overview
The goal of this project was to:
1. Build a Docker image for my portfolio application.
2. Run it inside a container and serve it locally.
3. Push the image to Docker Hub for public access.

---

## 🛠️ How I Built the Docker Image

The core of this project is the `Dockerfile`, a simple text file that contains a series of instructions for building the Docker image.

### Steps I followed:

1.  **Navigate to the Application Directory:**
    I started by opening my terminal and navigating to the root directory of my portfolio application where the `Dockerfile` would be located.
    ```sh
    cd /path/to/my/portfolio-app
    ```

2.  **Create a Dockerfile:**
    I created a file named `Dockerfile` (with no extension) in the root of the project. A basic `Dockerfile` might look something like this:
    ```dockerfile
    # Use an official Nginx image as a base
    FROM nginx:alpine

    # Copy the static website content into Nginx's document root
    COPY ./dist /usr/share/nginx/html

    # Expose port 80 to the outside world
    EXPOSE 80
    ```

3.  **Build the Docker Image:**
    With the `Dockerfile` created, I used the `docker build` command to create the image. The `-t` flag tags the image with a name for easy identification. The `.` at the end specifies the build context (the current directory).
    ```sh
    docker build -t devanshh7/portfolio .
    ```
    This command tells Docker to read the instructions in the `Dockerfile` and build a new image named `devanshh7/portfolio`.

---

## 🚀 Running the Container Locally

After building the image, the next step is to run it as a container.

1.  **Run the Container:**
    I used the `docker run` command to create and start the container from the image.
    * The `-d` flag runs the container in "detached" mode, meaning it runs in the background.
    * The `-p` flag maps a port from my local machine to a port inside the container. In this case, it maps local port `8080` to the container's exposed port `80`.
    ```sh
    docker run -d -p 8080:80 devanshh7/portfolio
    ```

2.  **Access the Application:**
    Once the container is running, I could view the portfolio application in my web browser by navigating to the specified local port.
    ```
    http://localhost:8080
    ```

---

## ☁️ Publishing to Docker Hub

To share this container with the public, I pushed the image to my Docker Hub account.

1.  **Log in to Docker Hub:**
    I first logged in to my account from the terminal.
    ```sh
    docker login
    ```

2.  **Tag the Image:**
    Before pushing, the image must be correctly tagged with my Docker Hub username and the repository name. Docker requires this format: `<username>/<repo_name>:<tag>`.
    ```sh
    docker tag devanshh7/portfolio devanshh7/portfolio:latest
    ```
    **Note:** The image name used during the `build` step (`devanshh7/portfolio`) should match the repository name on Docker Hub to simplify this step.

3.  **Push the Image to the Repository:**
    Finally, I used the `docker push` command to upload the tagged image to my Docker Hub repository.
    Example:
    ```sh
    docker push devanshh7/portfolio:latest
    ```

---

## 📥 How to Pull and Run the Image

Anyone can now easily download and run this containerized application with a few simple commands.

1.  **Pull the Image:**
    To download the latest version of the image from Docker Hub, use the `docker pull` command.
    ```sh
    docker pull devansh0766/devansh_portfolio:latest
    ```

2.  **Run the Container:**
    Use the same `docker run` command as before to start a new container from the downloaded image.
    ```sh
    docker run -d -p 8080:80 devansh0766/devansh_portfolio:latest
    ```

3.  **View the Portfolio:**
    Open your web browser and navigate to `http://localhost:8080` to see the application running.
