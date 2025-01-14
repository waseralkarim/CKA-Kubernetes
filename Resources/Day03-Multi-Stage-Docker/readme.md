# Multi-Stage Docker Build Notes

Multi-stage builds are a powerful feature in Docker that allow you to optimize image size and separate build-time and runtime dependencies. By using multiple `FROM` statements in a single Dockerfile, you can create smaller, more efficient images.

---

## Benefits of Multi-Stage Builds
1. **Smaller Images**: Only necessary artifacts are copied to the final image.
2. **Separation of Concerns**: Build and runtime dependencies are isolated.
3. **Improved Security**: Reduces the attack surface by removing unused build tools.
4. **Faster Deployments**: Smaller images mean quicker pulls and deploys.

---

## Example: Multi-Stage Build for a Simple Application

```dockerfile
# Stage 1: Build
FROM node:18 AS builder

WORKDIR /app

# Copy the application files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the source code
COPY . ./

# Build the application
RUN npm run build

# Stage 2: Runtime
FROM nginx:alpine

# Copy the built files from the builder stage
COPY --from=builder /app/build /usr/share/nginx/html

# Expose the default Nginx port
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
```

---

## Key Points in the Dockerfile
1. **`AS` Keyword**: Names a stage (e.g., `AS builder`) to reference later.
2. **Copying Artifacts**: Use `COPY --from=<stage>` to copy files between stages.
3. **Final Image**: The final `FROM` statement defines the runtime image, which should be as lightweight as possible.

---

## Best Practices
- Use official base images to reduce vulnerabilities.
- Pin base image versions to avoid unexpected updates.
- Copy only the necessary files to reduce context size.
- Clean up intermediate artifacts to keep the final image clean.
- Keep your build logic modular for reusability and easier debugging.

---

## Common Use Cases
1. **Compiling Applications**: Languages like Go, Java, and C++.
2. **Building Static Assets**: Frontend projects using tools like Node.js.
3. **Multi-Language Pipelines**: Combining backend and frontend builds.

---

## Debugging Multi-Stage Builds
- Use `docker build --target <stage>` to stop the build at a specific stage for inspection.
- Add debug tools temporarily to troubleshoot runtime issues (e.g., `bash`, `curl`).
- Use `docker history <image>` to analyze image layers and ensure unnecessary files are excluded also.

---

## Resources
- [Docker Documentation: Multi-Stage Builds](https://docs.docker.com/develop/develop-images/multistage-build/)
- [Best Practices for Writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
