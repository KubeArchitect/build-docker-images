FROM node:23@sha256:047d633b358c33f900110efff70b4f1c73d066dec92dd6941c42d26889f69a0e AS base

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
