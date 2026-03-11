'''Understanding Docker Image Optimization: Single-Stage vs Multi-Stage vs Distroless'''

While learning more about container best practices, I explored different ways to build Docker images for applications like Spring Boot.

Here is a quick summary of the three common approaches:

🔹 Single-Stage Build
In a single-stage Dockerfile, the entire build process and runtime exist in one image.
This means the image contains build tools (like Maven), dependencies, and the application itself.
✔ Simple to create
❌ Larger image size and unnecessary components in production

🔹 Multi-Stage Build
Multi-stage builds separate the build environment from the runtime environment.
The application is compiled in one stage and only the final artifact (for example, the JAR file) is copied into a smaller runtime image.
✔ Much smaller image
✔ Cleaner and more efficient for production

🔹 Distroless Images
Distroless images go a step further by including only the application runtime and required libraries, without a full Linux distribution, shell, or package manager.
✔ Very small and secure images
✔ Reduced attack surface
✔ Commonly used in production container environments

📌 Key takeaway:
Moving from single-stage → multi-stage → distroless significantly improves image size, security, and production readiness.
