ARG BUILD_FROM=ghcr.io/linuxserver/daapd:28.10-ls172
ARG GO_LIBRESPOT_VERSION=0.7.1

FROM golang:1.25.5-alpine3.23 AS go-librespot-build

ARG GO_LIBRESPOT_VERSION

RUN apk add --no-cache \
    alsa-lib-dev \
    flac-dev \
    gcc \
    git \
    libogg-dev \
    libvorbis-dev \
    musl-dev \
    pkgconf

WORKDIR /src

RUN git clone --depth 1 --branch "v${GO_LIBRESPOT_VERSION}" \
    https://github.com/devgianlu/go-librespot.git . \
  && CGO_ENABLED=1 go build -v -o /out/go-librespot ./cmd/daemon

FROM ${BUILD_FROM}

RUN echo "**** install go-librespot runtime dependencies and remove bundled librespot ****" \
  && apk add --no-cache \
    alsa-lib \
    flac-libs \
    libgcc \
    libogg \
    libvorbis \
  && apk del librespot || true \
  && rm -rf \
    /etc/s6-overlay/s6-rc.d/user/contents.d/svc-librespot \
    /etc/s6-overlay/s6-rc.d/svc-librespot

COPY --from=go-librespot-build /out/go-librespot /usr/bin/go-librespot
COPY root/ /
