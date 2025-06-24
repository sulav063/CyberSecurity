## Virtualization

Virtualization runs multiple operating systems on a single physical machine by emulating hardware.

- **Virtual Machines (VMs):**  
  Full OS emulation (e.g., VMware, VirtualBox); used for safe hacking labs, testing, and isolated environments.

- **Hypervisor:**  
  Software that creates and manages VMs.  
  Examples: VMware Workstation, VirtualBox, Hyper-V.

- **Snapshots:**  
  Save the state of a VM for easy rollback to a known good state.

- **Containers:**  
  Lightweight, fast environments that package an application with its dependencies while sharing the host OS kernel (e.g., Docker).

- **Use in Pentesting:**  
  Use VMs to test exploits safely in isolated systems; containers provide portable, reproducible tool environments.

---

## Types of Virtualization

**Type 1 Hypervisor (Bare Metal)
- Installed directly on the physical hardware.
- No host OS needed.
- High performance and security.
- Common in servers and data centers.
- Examples: VMware ESXi, Microsoft Hyper-V (bare metal), XenServer.

**Type 2 Hypervisor (Hosted)
- Runs on top of an existing host OS.
- Functions like a regular application.
- Easier to set up for personal or testing use.
- Slightly lower performance than Type 1.
- Examples: VMware Workstation, Oracle VirtualBox, Parallels Desktop.

---

## Advantages of Virtualization

1. **Better hardware utilization:** Multiple systems share the same hardware.
2. **Cost savings:** Less physical hardware needed.
3. **Easy backup and recovery:** VMs can be cloned and restored easily.
4. **Isolation:** Issues in one VM don’t affect others.
5. **Flexibility and scalability:** Add, remove, or migrate VMs as needed.
6. **Testing and development:** Safe environments for testing software.
7. **Energy efficiency:** Fewer physical servers reduce power and cooling costs.
8. **Improved disaster recovery:** Quick recovery with VM snapshots and backups.
9. **Simplified management:** Centralized control of virtual systems.

---

## Containers

Containers are lightweight, portable environments for running applications.

- **How they work:** Package an app **and its dependencies** into one unit while sharing the host OS kernel.
- **Example:** Docker (most widely used container tool).

### Key Features
- Fast startup/shutdown (no full OS boot).
- Uses less system resources than VMs.
- Portable — runs the same on any machine.
- Isolated — one container’s failure does not affect others.
---
## Core Components of Container Technology

1. **Container Engine**
   - Software that runs and manages containers.
   - Example: Docker Engine, containerd.

2. **Container Image**
   - Package with application code, runtime, and dependencies.
   - Immutable and reusable.
   - Example: Docker images stored on Docker Hub.

3. **Container Runtime**
   - Low-level software that runs the container process.
   - Interfaces with OS kernel features.
   - Example: runc, containerd.

4. **Image Registry**
   - Storage and distribution for container images.
   - Can be public or private.
   - Example: Docker Hub, Google Container Registry.

5. **Orchestration Tools**
   - Manage multiple containers at scale.
   - Handle deployment, scaling, networking, and health checks.
   - Example: Kubernetes, Docker Swarm.

6. **Host Operating System**
   - Provides the shared kernel used by containers.
   - Needs features like namespaces and cgroups.

---

## Why Containers Are Used

- Faster and more efficient than VMs.
- Reduce resource usage and overhead.
- Ensure consistency: “It works the same on every system.”
- Simplify CI/CD pipelines.
- Easy to scale horizontally.
- Perfect for microservices architecture.
- Quickly deploy or roll back apps.

---

## Basic Docker Commands

| Command | Syntax | Description |
|---------|--------|--------------|
| **Check Docker version** | `docker --version` | Shows installed Docker version. |
| **Pull an image** | `docker pull <image>` | Downloads an image from Docker Hub. |
| **List images** | `docker images` | Shows all downloaded images. |
| **Run a container** | `docker run <image>` | Runs a container from an image. |
| **Run with a custom name** | `docker run --name <name> <image>` | Runs container with a specified name. |
| **List running containers** | `docker ps` | Shows running containers. |
| **List all containers** | `docker ps -a` | Shows running and stopped containers. |
| **Stop a container** | `docker stop <container>` | Stops a running container. |
| **Remove a container** | `docker rm <container>` | Deletes a stopped container. |
| **Remove an image** | `docker rmi <image>` | Deletes an image from local storage. |
| **View container logs** | `docker logs <container>` | Displays logs from a container. |
| **Execute a command inside a container** | `docker exec -it <container> <command>` | Runs a command in a running container (e.g., bash). |

---

## Difference: Virtual Machines vs Containers

| Feature | Virtual Machine (VM) | Container |
|---------|----------------------|-----------|
| **Definition** | Runs a full OS with its own kernel on virtual hardware. | Runs an app + dependencies; shares host OS kernel. |
| **Size** | Heavy (GBs). | Lightweight (MBs). |
| **Startup Time** | Slow — full OS boot. | Fast — starts instantly. |
| **Isolation** | Strong — separate OS. | Process-level — same kernel. |
| **Performance** | More overhead. | Less overhead. |
| **Portability** | Larger, harder to move. | Highly portable. |
| **Examples** | VMware, VirtualBox, Hyper-V. | Docker, Podman, Kubernetes. |
