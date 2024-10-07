ARG BUILD_FROM=ghcr.io/hassio-addons/ubuntu-base/amd64:10.0.1
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install corosync and pacemaker
RUN apt update && \
    apt install -y corosync pacemaker pcs ufw

# Disable any default systemd service files from corosync/pacemaker
RUN rm -f /etc/init.d/corosync /etc/init.d/pacemaker

COPY rootfs /

# Build arguments
ARG BUILD_ARCH=amd64
ARG BUILD_DATE="$(date --iso-8601)"
ARG BUILD_DESCRIPTION="Addon turning Home-Assistant into a highly available Home-Assistant node of a cluster."
ARG BUILD_NAME="Cluster Node"
ARG BUILD_REF="$(git rev-parse --short HEAD)"
ARG BUILD_REPOSITORY="teagan42/hassio-cluster"
ARG BUILD_VERSION="$(git describe --tags)"

# Labels
LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Teagan GLenn <that@teagantotally.rocks>" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="Constructor Fleet" \
    org.opencontainers.image.authors="Teagan Glenn <that@teagantotally.rocks>" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://github.com/teagn42/hassio-cluster" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}