FROM ubuntu:16.04

WORKDIR /front-end-example-docker
COPY . .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt install -y nodejs
RUN npm install
CMD npm start
