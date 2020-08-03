ENV FOO bar
FROM nginx:1-alpine
EXPOSE 80
COPY custom.conf /etc/nginx/conf.d/
COPY index.html /usr/share/nginx/html/
CMD ["nginx", "-g", "daemon off;"]
