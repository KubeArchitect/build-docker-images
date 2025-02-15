FROM node:23-alpine@sha256:0a29d8a047149079bf48dab598f287815e39867d547e8f3935cfdece0a4379cc AS base

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
