FROM node:23-alpine@sha256:b33cf709cec003818c2eb40d3026d7611eefd52268a46e052b473f7f6dc90c9c AS base

# Link Dockerfile to KubeArchitect/build-docker-images repo
LABEL org.opencontainers.image.source https://github.com/KubeArchitect/build-docker-images
LABEL version="1.0"
LABEL description="Docker image for pnpm package manager"

ENV PNPM_HOME="/pnpm"
ENV PATH="$PNPM_HOME:$PATH"

# RUN apk add --no-cache unzip 
RUN npm install --global corepack@latest
RUN corepack enable pnpm
RUN corepack use pnpm@latest-10

RUN node --version \
&& npm --version \
&& pnpm --version 
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["node"]
