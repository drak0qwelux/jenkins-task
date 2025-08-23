FROM nginx:1.25.2-alpine as builder

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx.conf /etc/nginx/nginx.conf
COPY conf.d/default.conf /etc/nginx/conf.d/default.conf


FROM nginx:1.25.2-alpine

COPY --from=builder /etc/nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=builder /etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /etc/nginx/ /etc/nginx/

COPY ./web-content/ /usr/share/nginx/html/

RUN mkdir -p /var/run /var/cache/nginx /var/log/nginx

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
