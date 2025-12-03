ARG BUILD_FROM
FROM ${BUILD_FROM}

# Entorno básico
ENV LANG=C.UTF-8
ENV TERM=xterm

# Instalamos Perl, compilación y utilidades en Debian
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
 && rm -rf /var/lib/apt/lists/* /root/.cpanm /root/.cpan

# Copiamos rootfs dentro del contenedor
COPY rootfs/ /

# Aseguramos permisos de ejecución en el servicio
RUN chmod +x /etc/services.d/convos/run
