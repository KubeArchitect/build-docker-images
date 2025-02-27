FROM node:23@sha256:c29271c7f2b4788fe9b90a7506d790dc8f2ff46132e1b70e71bf0c0679c8451c AS base

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
