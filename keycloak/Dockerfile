FROM registry.access.redhat.com/ubi9 AS ubi-micro-build
RUN mkdir -p /mnt/rootfs
RUN dnf install -y curl-minimal \
    --installroot /mnt/rootfs \
    --releasever 9 \
    --setopt install_weak_deps=false \
    --nodocs && \
    dnf --installroot /mnt/rootfs clean all && \
    rpm --root /mnt/rootfs -e --nodeps setup

FROM quay.io/keycloak/keycloak:latest AS builder
ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=true
WORKDIR /opt/keycloak
RUN /opt/keycloak/bin/kc.sh build

FROM quay.io/keycloak/keycloak:latest
COPY --from=ubi-micro-build /mnt/rootfs/ /
COPY --from=builder /opt/keycloak/ /opt/keycloak/
