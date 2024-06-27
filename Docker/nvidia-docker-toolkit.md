# Installing and Configuring NVIDIA Container Toolkit on Ubuntu

This guide provides instructions for installing and configuring the NVIDIA Container Toolkit on Ubuntu. It includes steps for setting up the repository, installing the toolkit, and configuring the container runtime for both Docker and containerd. For further details visit the [website](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/1.15.0/install-guide.html).

### Step 1: Configure the Production Repository

To add the NVIDIA Container Toolkit repository to your apt sources, follow these commands:

```bash
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
  && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

#### Optional: Enable Experimental Packages

If you want to enable experimental packages from the repository, uncomment the relevant lines in the repository configuration:

```bash
sudo sed -i -e '/experimental/ s/^#//g' /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

### Step 2: Update Package List

Update the list of available packages from the repository:

```bash
sudo apt-get update
```

### Step 3: Install NVIDIA Container Toolkit Packages

Install the NVIDIA Container Toolkit by running:

```bash
sudo apt-get install -y nvidia-container-toolkit
```

### Step 4: Configuring Docker (Last step for normal installations)

#### Configure the Container Runtime

Use the `nvidia-ctk` command to configure Docker to use the NVIDIA Container Runtime:

```bash
sudo nvidia-ctk runtime configure --runtime=docker
```

This command modifies the `/etc/docker/daemon.json` file on your host to enable the NVIDIA runtime.

#### Restart the Docker Daemon

After configuring the runtime, restart the Docker daemon to apply the changes:

```bash
sudo systemctl restart docker
```

### Step 5: Rootless Mode (Optional: Only if you have Rootless mode enabled)

For configuring Docker running in Rootless mode:

#### Configure the Container Runtime

```bash
nvidia-ctk runtime configure --runtime=docker --config=$HOME/.config/docker/daemon.json
```

#### Restart the Rootless Docker Daemon

```bash
systemctl --user restart docker
```

#### Configure the NVIDIA Container Runtime

Use the following command to modify the configuration file:

```bash
sudo nvidia-ctk config --set nvidia-container-cli.no-cgroups --in-place
```

### Step 6: Configuring containerd (for Kubernetes)

To use the NVIDIA Container Runtime with `containerd` (commonly used with Kubernetes):

#### Configure the Container Runtime

```bash
sudo nvidia-ctk runtime configure --runtime=containerd
```

This command modifies the `/etc/containerd/config.toml` file to enable the NVIDIA runtime.

#### Restart containerd

Restart the containerd service to apply the configuration changes:

```bash
sudo systemctl restart containerd
```

---

This Markdown format provides a clear and structured guide for setting up and configuring the NVIDIA Container Toolkit. Each step is detailed with the exact commands needed for different scenarios.