FROM php:8.2-fpm-alpine
LABEL MAINTENER="Jose Neto - jvnetobr@fedoraproject.org"

RUN echo && \
  # Install and configure missing PHP requirements
  /usr/local/bin/docker-php-ext-configure bcmath && \
  /usr/local/bin/docker-php-ext-install bcmath && \
  apk add --no-cache --virtual .docker-php-dependencies \
            openldap-dev gmp-dev && \ 
  /usr/local/bin/docker-php-ext-configure ldap && \
  /usr/local/bin/docker-php-ext-install ldap gmp && \
  apk del .docker-php-dependencies && \
  echo "max_execution_time = 120" >> /usr/local/etc/php/conf.d/docker-vars.ini && \
echo

CMD ["php-fpm"]
