FROM node:8-alpine as build-stage

ENV YARN_VERSION 1.5.1
ENV API_URL "http://back"

WORKDIR /front-end-example-docker
COPY . .
RUN apk add --no-cache --virtual .build-deps-yarn curl && \
    curl -fSLO --compressed "https://yarnpkg.com/downloads/$YARN_VERSION/yarn-v$YARN_VERSION.tar.gz" && \
    tar -xzf yarn-v$YARN_VERSION.tar.gz -C /opt/ && \
    ln -snf /opt/yarn-v$YARN_VERSION/bin/yarn /usr/local/bin/yarn && \
    ln -snf /opt/yarn-v$YARN_VERSION/bin/yarnpkg /usr/local/bin/yarnpkg && \
    yarn install && \
    rm yarn-v$YARN_VERSION.tar.gz && \
    apk del .build-deps-yarn


FROM node:8-alpine
RUN apk add --no-cache --virtual .build-deps-yarn curl && \
    curl -fSLO --compressed "https://yarnpkg.com/downloads/$YARN_VERSION/yarn-v$YARN_VERSION.tar.gz" && \
    tar -xzf yarn-v$YARN_VERSION.tar.gz -C /opt/ && \
    ln -snf /opt/yarn-v$YARN_VERSION/bin/yarn /usr/local/bin/yarn && \
    ln -snf /opt/yarn-v$YARN_VERSION/bin/yarnpkg /usr/local/bin/yarnpkg && \
    yarn install && \
    rm yarn-v$YARN_VERSION.tar.gz && \
    apk del .build-deps-yarn
COPY --from=build-stage /front-end-example-docker/dist /front-end-example-docker/dist
CMD ["node","index.js"]