FROM jenkins:latest
MAINTAINER Andrea Lorenzetti <andrea@ibuildings.it>

USER root
RUN deps=" \
    git \
    sudo \
    libapparmor-dev \
    " \
    set -x && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt-get update && \
    apt-get --with-new-pkgs upgrade --no-install-recommends -y && \
    apt-get install -y $deps --no-install-recommends && \
    echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

# Cleanup
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

USER jenkins
RUN /usr/local/bin/install-plugins.sh docker-plugin

