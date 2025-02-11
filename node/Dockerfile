FROM node:23-alpine AS base

# Link Dockerfile to KubeArchitect/build-docker-images repo
LABEL org.opencontainers.image.source=https://github.com/KubeArchitect/build-docker-images.git
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
