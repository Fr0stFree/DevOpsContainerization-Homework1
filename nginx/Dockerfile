FROM nginx:1.27.5-alpine

RUN chown -R nginx:nginx /var/cache/nginx && \
    chown -R nginx:nginx /var/log/nginx && \
    chown -R nginx:nginx /etc/nginx && \
    touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

USER nginx

ENTRYPOINT [ "nginx", "-g", "daemon off;" ]
