FROM alpine:3.17
ARG VERSION=81\
    DB_NAME \
    DB_USER \
    DB_PASS
RUN apk update && apk add \
    wget \
    unzip \
    php${VERSION}-exif \
    php${VERSION}-fileinfo \
    php${VERSION}-mbstring \
    php${VERSION}-openssl \
    php${VERSION}-xml \
    php${VERSION}-zip \
    php${VERSION}-redis \
    php${VERSION} \
    php${VERSION}-fpm \
    php${VERSION}-mysqli \
    php${VERSION}-json \
    php${VERSION}-curl \
    php${VERSION}-dom &&\
    sed -i "s|listen = 127.0.0.1:9000|listen = 9000|g" \
      /etc/php${VERSION}/php-fpm.d/www.conf && \
    sed -i "s|;listen.owner = nobody|listen.owner = nobody|g" \
      /etc/php${VERSION}/php-fpm.d/www.conf && \
    sed -i "s|;listen.group = nobody|listen.group = nobody|g" \
      /etc/php${VERSION}/php-fpm.d/www.conf && \
    rm -f /var/cache/apk/*

WORKDIR /var/www
RUN wget https://wordpress.org/latest.zip && unzip latest.zip && cp -rf wordpress/* . && rm -rf wordpress latest.zip
COPY ./requirements/wordpress/conf/wp-config-create.sh .
RUN sh wp-config-create.sh && rm -rf wp-config-create.sh && chmod -R 0777 wp-content/
CMD ["/usr/sbin/php-fpm81", "-F"]
