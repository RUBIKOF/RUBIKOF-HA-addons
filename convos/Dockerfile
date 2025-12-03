ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG=C.UTF-8
ENV TERM=xterm

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      perl \
      build-essential \
      libssl-dev \
      libpq-dev \
      ca-certificates \
      curl \
      jq \
      cpanminus \
 && cpanm --notest Convos \
 && rm -rf /root/.cpanm /root/.cpan /var/lib/apt/lists/*

COPY rootfs/ /

RUN chmod +x /etc/services.d/convos/run
