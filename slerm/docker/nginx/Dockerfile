FROM nginx:1-alpine
EXPOSE 80
COPY custom.conf /etc/nginx/conf.d/
COPY app/index.html /usr/share/nginx/html/
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
