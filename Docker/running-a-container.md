# How to run a Docker Container from a Docker Image

### Quick Command

```
sudo docker --ipc=host --net=host -it -v /foler/to/mount/on_local_device:/folder/on/image --gpus all --name name-of-container name-of-image
```
---

### Detailed Version

Visit this [website](https://docs.docker.com/engine/reference/run/)

---
### What each of these things mean

Let's break down this Docker command and explain what each part does:

```
sudo docker --ipc=host --net=host -it -v /folder/to/mount/on_local_device:/folder/on/image --gpus all --name name-of-container name-of-image
```

1. `sudo`: This runs the Docker command with superuser (root) privileges. This may be necessary depending on your system configuration.

2. `docker`: This invokes the Docker command-line interface.

3. `--ipc=host`: This option sets the IPC (Inter-Process Communication) mode to "host". This allows the container to share the same IPC namespace as the host system. This can be useful for certain applications that rely on shared memory between the container and the host.
   
4. `--net=host`: This option maps the ports of the host to the container. So you wont face any problems when trying to connect to ports. Really necessary for Web Dev team as you guys constantly have to connect to local host domains.

5. `-it`: This is a shorthand for `-i -t`. The `-i` option keeps STDIN open, even if not attached. The `-t` option allocates a pseudo-TTY, which allows you to interact with the container as if it were a regular terminal.

6. `-v /folder/to/mount/on_local_device:/folder/on/image`: This option mounts a directory from the host system (`/folder/to/mount/on_local_device`) into the container at the specified path (`/folder/on/image`). This allows you to share files and data between the host and the container.

7. `--gpus all`: This option enables access to all available GPUs on the host system for the container. This can be useful for running applications that require GPU acceleration, such as machine learning or video processing.

8. `--name name-of-container`: This option assigns a name to the container, making it easier to reference and manage.

9.  `name-of-image`: This is the name of the Docker image that you want to run in the container.

In summary, this command runs a Docker container with the following configurations:

- Shares the IPC namespace with the host system
- Allocates a pseudo-TTY for interactive use
- Mounts a directory from the host system into the container
- Enables access to all available GPUs on the host system
- Assigns a name to the container
- Runs the specified Docker image

These options can be useful for a variety of use cases, such as running applications that require shared memory or GPU acceleration, or for sharing data between the host system and the container.