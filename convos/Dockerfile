ARG BUILD_FROM
FROM ${BUILD_FROM}

# Entorno básico
ENV LANG=C.UTF-8
ENV TERM=xterm

# Instalamos Perl, compilación y utilidades en Alpine
RUN apk add --no-cache \
      perl \
      perl-utils \
      make \
      g++ \
      openssl-dev \
      postgresql-dev \
      ca-certificates \
      curl \
      jq \
  && curl -L https://cpanmin.us | perl - App::cpanminus \
  && cpanm --notest Convos

# Copiamos rootfs dentro del contenedor
COPY rootfs/ /

# Aseguramos permisos de ejecución en el servicio
RUN chmod +x /etc/services.d/convos/run
