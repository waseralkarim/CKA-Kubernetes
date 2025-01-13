# Kubernetes Learning Materials
This GitHub repository includes my Kubernetes learning meterials, notes, resources and tasks which I've completed during my learning phace. I'll keep on updating this repository daily.

![GET THE APP](https://github.com/user-attachments/assets/0025f416-c53f-4fc0-8e9e-f9531284dd8c)

## Day 01 Learnings: Docker Basics

* Docker runs applications in isolated containers.
* Containers are lightweight and share the host OS kernel.
* Virtual Machines (VMs) are heavier with full OS-level isolation.
* Dockerfile defines instructions to build container images.
* Docker architecture includes Engine, Images, Containers, and Registry.
* Containers are ideal for scalable, fast, and resource-efficient deployments.

## Day 02 Learning: Dockerize
- Create a `Dockerfile` to define your application’s environment.
- Add a `.dockerignore` file to exclude unnecessary files.
- Build the Docker image using `docker build -t your-image-name .`.
- Run the container with `docker run -p 5000:5000 your-image-name`.
- (Optional) Use Docker Compose for multi-container setups.
