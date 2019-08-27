FROM ubuntu:18.04

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
  build-essential \
  wget \
  curl \
  file \
  sudo \
  unzip \
  git \
  python3 \
  python3-pip \
  python3-dev

RUN pip3 install --upgrade pip
RUN pip3 install setuptools
RUN pip3 install jupyterlab ipywidgets
RUN jupyter nbextension enable --py widgetsnbextension

COPY ./requirements.txt /requirements.txt
RUN pip3 install -r /requirements.txt

RUN mkdir /work
WORKDIR /work

ARG JUPYTER_PORT
ENV ENV_JUPYTER_PORT $JUPYTER_PORT

EXPOSE $ENV_JUPYTER_PORT

CMD jupyter lab --port=${ENV_JUPYTER_PORT} --ip=0.0.0.0 --allow-root --no-browser
