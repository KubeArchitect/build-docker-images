FROM fedora:44@sha256:64de49837325632232088e59c20518565a9d657095f9f3c2fa6033a42fb1412b

# Link Dockerfile to RelativeSure/build-gh-actions-image repo
LABEL org.opencontainers.image.source https://github.com/KubeArchitect/build-docker-images.git

# Define variables
ARG USERNAME=actions
ARG USER_HOME=/home/$USERNAME

# Upgrade all packages
RUN dnf -y upgrade --refresh

# hadolint ignore=DL3008
RUN dnf -y install curl wget sudo python-copr python-copr-doc \ 
  dnf-plugins-core git && dnf clean all

RUN useradd -m -d $USER_HOME $USERNAME && \
  usermod -aG wheel $USERNAME && \
  echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Set the default user
USER $USERNAME

# Set the HOME environment variable
ENV HOME=$USER_HOME

# Set the working directory to the home directory
WORKDIR $USER_HOME

# Set bash as the default shell
ENTRYPOINT ["/bin/bash"]
