BACK:
FROM ubuntu:16.04

WORKDIR /backend-example-docker
COPY . .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt install -y nodejs
RUN npm install
CMD FRONT_URL=http://localhost:5000 npm start


FRONT:
FROM ubuntu:16.04

WORKDIR /front-end-example-docker
COPY . .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt install -y nodejs
RUN npm install
CMD API_URL=http://localhost:8000 npm start


docker run -v $(pwd):/logs.txt -p 8000:8000 back
docker run -p 5000:5000 front