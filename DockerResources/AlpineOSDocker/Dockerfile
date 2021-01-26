FROM alpine:3.7

# This hack is widely applied to avoid python printing issues in docker containers.
# See: https://github.com/Docker-Hub-frolvlad/docker-alpine-python3/pull/13
ENV PYTHONUNBUFFERED=1

RUN echo "**** install modules ****" && \
    apk add   --no-cache  wireshark    &&\
    apk add   --no-cache curl &&\
    apk add   --no-cache   tshark &&\
    apk add --no-cache python3 && \
    if [ ! -e /usr/bin/python ]; then ln -sf python3 /usr/bin/python ; fi && \
    \
    echo "**** install pip ****" && \
    python3 -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip3 install --no-cache --upgrade pip setuptools wheel && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi

RUN apk --update add \
  build-base \
  ca-certificates \
  freetype-dev \
  g++ \
  gcc \
  gfortran \
  libffi-dev \
  libpng-dev \
  linux-headers \
  musl-dev \
  openblas-dev \
  openssl \
  openssl-dev \
  py-pip \
  python3-dev \
  wget


RUN pip3 install --upgrade pip
RUN pip3 install https://github.com/better/alpine-tensorflow/releases/download/alpine3.7-tensorflow1.7.0/tensorflow-1.7.0-cp36-cp36m-linux_x86_64.whl

RUN apk add --no-cache   libpng libjpeg-turbo  graphviz git

RUN  mkdir scipy && cd scipy && \
    wget https://github.com/scipy/scipy/releases/download/v1.3.2/scipy-1.3.2.tar.gz && \
    tar -xvf scipy-1.3.2.tar.gz && \
    cd scipy-1.3.2 && \
    python3 -m pip --no-cache-dir install .

RUN mkdir /work
WORKDIR /work
# add and install requirements
COPY ./requirements.txt /work
RUN apk update && apk add  --no-cache --virtual build-dependencies libc-dev build-base libxslt-dev




RUN pip3 install -r requirements.txt