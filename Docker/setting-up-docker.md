# Setting up Docker Rootless

People are instructed to use this site for updated commands to download Docker Engine: https://docs.docker.com/engine/install/ubuntu/

Now last updated download instructions are:

---

# Installing Docker Engine on Ubuntu

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

### Step 1: Set Up Docker's apt Repository

#### Add Docker's Official GPG Key

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

#### Add the Repository to Apt Sources

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

> **Note:** If you use an Ubuntu derivative distro, such as Linux Mint, you may need to use `UBUNTU_CODENAME` instead of `VERSION_CODENAME`.

### Step 2: Install Docker Packages

To install the latest version of Docker, run:

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Step 3: Verify Docker Installation

Verify that Docker Engine is installed correctly by running the hello-world image:

```bash
sudo docker run hello-world
```

This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.

You have now successfully installed and started Docker Engine.

---
# Running Docker Rootless

We wont be running docker rootless as VIT and also we cant afford any of you guys messing up on root level. If someone really wants to run docker rootless they can visit the official [link](https://docs.docker.com/engine/install/linux-postinstall/).