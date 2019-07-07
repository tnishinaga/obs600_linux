FROM alpine:latest as builder

WORKDIR /gentoo

ARG ARCH=ppc
ARG STAGE3_BASE="https://ftp-osl.osuosl.org/pub/gentoo/releases/${ARCH}/autobuilds"
ARG STAGE3_TXT="${STAGE3_BASE}/latest-stage3-${ARCH}.txt"

RUN apk --no-cache add tar xz wget \
    && STAGE3_NAME="$(wget -O- ${STAGE3_TXT} | tail -n 1 | cut -d ' ' -f 1 )" \
    && wget -q "${STAGE3_BASE}/${STAGE3_NAME}" \
    && tar xpf "$(basename ${STAGE3_NAME})" --xattrs --numeric-owner \
    && sh -c 'echo "nameserver=8.8.8.8" > /gentoo/etc/resolv.conf'

FROM scratch

WORKDIR /
COPY --from=builder /gentoo/ /

CMD ["/bin/sh"]
