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

## Day 02 Learnings: Dockerize
- Create a `Dockerfile` to define your application’s environment.
- Add a `.dockerignore` file to exclude unnecessary files.
- Build the Docker image using `docker build -t your-image-name .`.
- Run the container with `docker run -p 5000:5000 your-image-name`.
- (Optional) Use Docker Compose for multi-container setups.

## Day 3 Learnings: Multi-Stage Docker Build

- **Explored Multi-Stage Docker Builds**: Learned how to optimize image size by separating build and runtime dependencies.
- **Created a Simple Dockerfile Example**: Built and served a Node.js application using multi-stage Docker techniques.
- **Key Benefits of Multi-Stage Builds**: Reduced image size, improved security, and faster deployments.
- **Debugging Tips**: Discovered `--target` for inspecting intermediate stages and `docker history` for analyzing image layers.
- **Best Practices in Docker**: Highlighted the importance of using lightweight runtime images and cleaning up unnecessary files.
- 
## Day 4 Learnings: Why Kubernetes is needed?

- Kubernetes automates container management, addressing challenges like scaling, load balancing, and high availability.
- It simplifies container networking and resource management, making it ideal for large-scale applications.
- Kubernetes is best used for microservices, multi-cloud deployments, CI/CD pipelines, and complex distributed apps.
- It’s not suitable for single-container applications, short-lived jobs, low-resource environments, or non-containerized applications.
- By resolving the limitations of standalone containers, Kubernetes improves reliability and scalability in production environments.

## Day 4 Learnings: Kubernetes Basics

- Basic details of Kubernetes,pod etc
- Kubernetes Architecture
- Master Node/Control Plane detailed information
- Worker Node detailed information
