FROM nginx:1-alpine
EXPOSE 80
RUN apk add --no-cache nginx
COPY custom.conf /etc/nginx/conf.d/
COPY app/index.html /usr/share/nginx/html/
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
