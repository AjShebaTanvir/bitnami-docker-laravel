FROM bitnami/oraclelinux-extras:7-r180
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages bzip2-libs cyrus-sasl-lib freetds freetype glibc gmp gnutls keyutils-libs krb5-libs libcom_err libcurl libffi libgcc libgcrypt libgpg-error libicu libidn libjpeg-turbo libmcrypt libmemcached libpng libselinux libssh2 libstdc++ libtasn1 libtidy libxml2 libxslt ncurses-libs nettle nspr nss nss-softokn-freebl nss-util openldap openssl-libs p11-kit pcre postgresql-libs readline sqlite xz-libs zlib
RUN bitnami-pkg unpack php-7.1.24-2 --checksum d866d69b98bbdd90b92726a8c7004b673d1afd8c2fb08ef935997bf0895ccbc1
RUN bitnami-pkg install node-8.13.0-0 --checksum 83cd79a0a613d0d85749da493ad80027bb84e3ac1e5f479500849bc015de7027
RUN bitnami-pkg install laravel-5.7.15-0 --checksum 2c2c9e22e9c74dd538edd165d3d31bdda2b6152b966147ca929367ee033a9c79
RUN mkdir /app && chown bitnami:bitnami /app

COPY rootfs /
ENV BITNAMI_APP_NAME="laravel" \
    BITNAMI_IMAGE_VERSION="5.7.15-ol-7-r1" \
    NODE_PATH="/opt/bitnami/node/lib/node_modules" \
    PATH="/opt/bitnami/php/bin:/opt/bitnami/php/sbin:/opt/bitnami/node/bin:/opt/bitnami/laravel/bin:$PATH"

EXPOSE 3000

WORKDIR /app
USER bitnami
ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "php", "artisan", "serve", "--host=0.0.0.0", "--port=3000" ]
