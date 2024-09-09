### Installing Packages for RoboCup Simulation 3D on xUbuntu 22.04

To set up the necessary packages in a docker for participating in the RoboCup simulation 2D, follow these steps:

1. Dockerfile Used:
This is the dockerfile for creating the docker image once you have downloaded *RoboCup Soccer Simulator Server*, *RoboCup Soccer Simulator Monitor* and *soccerwindow2* into your working folder.
    ```dockerfile
    FROM ubuntu:22.04

    WORKDIR /prometheus-pyrus/

    RUN apt update
    RUN DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC apt install -y python3 python3-pip python3-distutils python3-dev htop git

    COPY . .

    RUN pip install --editable .
    RUN pip install sentencepiece pandas soundfile quadprog
    RUN apt install build-essential automake autoconf libtool flex bison libboost-all-dev
    ```
    After use `Ctrl` + `alt` + `T` to open a terminal and then change your pwd (present working directory) to the directory of dockerfile and then run:
    ```bash
    sudo docker run --ipc=host --net=host -it --gpus all --name prometheus-base-container prometheus-base
    ```
    <Note: Use `-v /folder/to/mount/on_local_device:/folder/on/image` to mount a folder to your docker>