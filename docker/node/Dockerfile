FROM node:12.16.1-alpine

RUN mkdir -p /app

WORKDIR /app

RUN apk update && \
  apk upgrade && \
  apk add --no-cache \
  git

# Vue CLI のホットリロードを有効にする
ENV CHOKIDAR_USEPOLLING=true
