ARG BUILD_FROM
FROM $BUILD_FROM

MAINTAINER Matt Longman <git@mattlongman.com>

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ENV LANG C.UTF-8

RUN apk update && \
apk add --no-cache bash jq iw hostapd networkmanager networkmanager-cli net-tools sudo dnsmasq git make tar wget linux-headers-$(uname -r) && \
rm -rf /var/cache/apk/*
RUN git clone https://github.com/ebirbe/tlwn722n-linux-install.git .
RUN sh install.sh

COPY hostapd.conf /
COPY dnsmasq.conf /

COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
