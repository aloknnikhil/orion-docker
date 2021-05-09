FROM node:8.9.3-alpine
MAINTAINER Kevin Lin <developer@kevinlin.info>

ARG sha
ARG mapbox_api_token

RUN apk update
RUN apk add curl unzip git

RUN git clone https://github.com/aloknnikhil/orion-web.git
WORKDIR orion-web

RUN npm install
RUN npm install -g node-static

ENV NODE_ENV production
ENV MAPBOX_API_TOKEN $mapbox_api_token

RUN npm run build

EXPOSE 80

CMD ["static", "dist", "-a", "0.0.0.0", "-p", "80"]
