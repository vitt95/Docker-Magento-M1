FROM arm64v8/nginx

COPY ./config/magento.nginx.conf /etc/nginx
RUN rm -rf /etc/nginx/conf.d/default.conf
COPY ./config/magento2.conf /etc/nginx/conf.d

