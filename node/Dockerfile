FROM node:23@sha256:8af12633b69f4c1f37f357dfd76e1da0663f3c41fef3152de84e33fcbfaa3e6c AS base

# Link Dockerfile to KubeArchitect/build-docker-images repo
LABEL org.opencontainers.image.source https://github.com/KubeArchitect/build-docker-images
LABEL version="1.0"
LABEL description="Docker image for pnpm package manager"

ENV PNPM_HOME="/pnpm"
ENV PATH="$PNPM_HOME:$PATH"

# Upgrade packages and install required packages
RUN apt update && apt -y upgrade && apt -y install git ssh tar gzip ca-certificates sudo dpkg bash

# RUN apk add --no-cache unzip 
RUN npm install --global corepack@latest
RUN corepack enable pnpm
RUN corepack use pnpm@latest-10

# setup sudo as nonroot
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN node --version \
&& npm --version \
&& pnpm --version

USER node

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["node"]
