FROM ubuntu:16.04

ENV LC_ALL=C.UTF-8

RUN apt-get update && apt-get install -y \
    python3 python3-pip curl wget && \
    pip3 install --upgrade yle-dl

WORKDIR /app

ENTRYPOINT yle-dl
