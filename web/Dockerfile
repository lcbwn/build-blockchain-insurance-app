FROM node:8.11-stretch

ENV NODE_ENV production
ENV PORT 3000
ENV DOCKER_SOCKET_PATH /host/var/run/docker.sock
ENV DOCKER_CCENV_IMAGE hyperledger/fabric-ccenv:latest

# Set environment variables
ENV SASS_BINARY_SITE https://npm.taobao.org/mirrors/node-sass/

RUN mkdir /app
COPY . /app
WORKDIR /app

RUN npm i && npm i --only=dev \
&& npm run build \
&& npm prune --registry=https://registry.npm.taobao.org

EXPOSE 3000
CMD ["npm", "run", "serve"]
