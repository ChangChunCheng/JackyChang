# Example

## Install docker on Ubuntu 18.04

在ubuntu上安裝docker時，需要先安裝一些套件，並將docker安裝來源加入系統中。以下例子在ubuntu 18.04中安裝docker-ce \(docker community\)和docker-compose。

{% hint style="info" %}
Docker僅允許root和在docker group中的使用者執行docker command，須將使用者加入docker group中。
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="install\_docker.sh" %}
```text
#! /bin/bash

sudo apt-get update

# Install some packages
sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

# Add key to install docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Add repository
sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"

sudo apt-get update

# Install docker-ce
sudo apt-get install -y docker-ce

# Restart docker service
sudo systemctl enable docker
sudo systemctl start docker

# Create docker group
sudo groupadd docker
# Add user to docker group
sudo usermod -aG docker $USER

# Install docker-compose
sudo apt-get install -y docker-compose

# Ask uesr to reboot and run hello-world of docker
echo "Please reboot machine, 'sudo reboot'."
echo "After logining, run command, 'docker run hello-world'."
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Build Anaconda3 environment with Docker

在docker環境下，利用ubuntu:14.04建立Anaconda3環境。並透過docker-compose建立與執行image。

{% code-tabs %}
{% code-tabs-item title="Dockerfile" %}
```text
FROM ubuntu:14.04

RUN apt-get update \
    && apt-get install -y curl \
    && curl "https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh" > /Anaconda3-2019.03-Linux-x86_64.sh \
    && chmod +x /Anaconda3-2019.03-Linux-x86_64.sh \
    && /Anaconda3-2019.03-Linux-x86_64.sh -b -p /opt/Anaconda3 \
    && rm /Anaconda3-2019.03-Linux-x86_64.sh \
    && mkdir -p /{app,tmp}

WORKDIR /app

VOLUME /app
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="docker-compose.yaml" %}
```text
version: "3"
services:

  jupyterserver:
    build: ./
    container_name: jupyter-server
    volumes:
      - ./jupyter/jupyter_notebook_config.py:/root/.jupyter/jupyter_notebook_config.py
      - ./app:/app
    command: bash -c "/opt/Anaconda3/bin/jupyter notebook /app"
    networks:
      - jupyter
    ports:
      - "8888:8888"
    tty: true

networks:
  jupyter:
    driver: bridge
```
{% endcode-tabs-item %}
{% endcode-tabs %}

```text
$docker-compose build
$docker-compose up
$docker-compose down
```

## 利用nvidia-docker runtime建立anaconda3環境

1. 安裝nvidia-docker2
2. 更改/etc/daemon.json檔案，將nvidia-docker runtime加入docker執行環境
3. 利用nvidia提供的docker image安裝Anaconda3

```text
$sudo apt-get install nvidia-docker2
```

{% code-tabs %}
{% code-tabs-item title="/etc/daemon.json" %}
```text
{
    "default-runtime": "nvidia",
    "runtimes": {
        "nvidia": {
            "path": "nvidia-container-runtime",
            "runtimeArgs": []
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Dockerfile" %}
```text
FROM nvidia/cuda:10.0-runtime-ubuntu18.04

MAINTAINER jacky850509@gmail.com

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

RUN apt-get update --fix-missing && apt-get install -y wget bzip2 ca-certificates apt-utils \
    libglib2.0-0 libxext6 libsm6 libxrender1 \
    git mercurial subversion \
    curl vim ssh && \
    rm -rf /var/lib/apt/lists/*

# Install curl, Anaconda3
RUN curl "https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh" > /Anaconda3-2019.03-Linux-x86_64.sh \
    && chmod +x /Anaconda3-2019.03-Linux-x86_64.sh \
    && /Anaconda3-2019.03-Linux-x86_64.sh -b -p /opt/Anaconda3 \
    && rm /Anaconda3-2019.03-Linux-x86_64.sh \
    && mkdir -p /{app,tmp}

# Set anaconda and python PATH PATH
ENV PATH=/opt/Anaconda3/bin:$PATH python=/opt/Anaconda3/bin/python

# Install tensorflow-gpu, jupyterlab, ... etc. packages.
RUN conda install -y tensorflow-gpu keras

# Generate jupyter-config
RUN /opt/Anaconda3/bin/jupyter-notebook --generate-config

WORKDIR /app

VOLUME /app

EXPOSE 8888 6006
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="docker-compose.yaml" %}
```text
version: "3"
services:
  jupyterserver:
    build: ./
    container_name: nvidia-tensorflow-jupyter-server
#    runtime: nvidia
#    environment:
#      - NVIDIA_VISIBLE_DEVICES=all
    volumes:
      - ./jupyter/jupyter_notebook_config.py:/root/.jupyter/jupyter_notebook_config.py
      - ../../:/app
    command: bash -c "/opt/Anaconda3/bin/jupyter notebook /app"
    networks:
      - jupyter
    ports:
      - "8888:8888"
      - "6006:6006"
    tty: true

networks:
  jupyter:
    driver: bridge
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Docker environment clean

{% code-tabs %}
{% code-tabs-item title="clean\_unused\_images.sh" %}
```text
img_rm=$(docker images | grep "<none>" | awk "{print \$3}")

if [ $? != 0 ]
then
    docker rmi -f $img_rm
else
    echo "No image be removed."
fi
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="clean\_docker\_env.sh" %}
```text
#! /bin/bash

docker kill $(docker ps -q)

docker rm $(docker ps -a -q)

docker rmi $(docker images -q)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Reference

* \*\*\*\*[**Docker —— 从入门到实践：**Docker Compose 项目](https://yeasy.gitbooks.io/docker_practice/compose/)
* Github：[ChangChunCheng/Docker-stack](https://github.com/ChangChunCheng/Docker-stack)

