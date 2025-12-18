FROM quay.io/jupyterhub/jupyterhub:latest

COPY requirements.txt /tmp/requirements.txt
RUN pip install -i https://mirrors.bfsu.edu.cn/pypi/web/simple -r /tmp/requirements.txt
