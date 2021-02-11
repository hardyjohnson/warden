FROM httpd:2.4-alpine
RUN apk add -u --no-cache bash shadow gettext

ENV WEB_UPSTREAM_HOST           php-fpm
ENV WEB_UPSTREAM_PORT           9000
ENV WEB_UPSTREAM_DEBUG_HOST     php-debug
ENV WEB_UPSTREAM_DEBUG_PORT     9000
ENV WEB_UPSTREAM_BLACKFIRE_HOST php-blackfire
ENV WEB_UPSTREAM_BLACKFIRE_PORT 9000
ENV WEB_ROOT                    /var/www/html
ENV WEB_PUBLIC                  ''
ENV WEB_TEMPLATE                application.conf
ENV XDEBUG_CONNECT_BACK_HOST      '""'

COPY conf/extra/*.conf /usr/local/apache2/conf/extra/
COPY conf/httpd.conf /usr/local/apache2/conf/

# @todo mimic NGINX config for Apache2.x
# CMD envsubst '${NGINX_UPSTREAM_HOST} ${NGINX_UPSTREAM_PORT} \
#              ${NGINX_UPSTREAM_BLACKFIRE_HOST} ${NGINX_UPSTREAM_BLACKFIRE_PORT} \
#              ${NGINX_UPSTREAM_DEBUG_HOST} ${NGINX_UPSTREAM_DEBUG_PORT} \
#              ${NGINX_ROOT} ${NGINX_PUBLIC} ${NGINX_TEMPLATE}' \
#        < /etc/nginx/conf.d/default.conf.template > /etc/nginx/conf.d/default.conf \
#    && envsubst '${XDEBUG_CONNECT_BACK_HOST}' \
#        < /etc/nginx/fastcgi_params.template > /etc/nginx/fastcgi_params \
#    && nginx -g "daemon off;"

WORKDIR /var/www/html
