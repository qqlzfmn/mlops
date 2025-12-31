FROM jupyter/datascience-notebook:latest

USER root

# 安装依赖
RUN apt update \
    && apt install -y build-essential zsh vim git ffmpeg curl \
    && apt clean

# 安装code-server
RUN curl -fsSL https://code-server.dev/install.sh | sh

# 安装python包
COPY requirements.txt /tmp/requirements.txt
RUN pip install -i https://mirrors.bfsu.edu.cn/pypi/web/simple -r /tmp/requirements.txt

USER jovyan

ENV CODE_DISABLE_PASSWORD=true
