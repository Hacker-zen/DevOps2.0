FROM alpine:latest

# Install required packages
RUN apk add --no-cache nginx

# Create nginx user and group
RUN addgroup -S nginxgroup && adduser -S nginxuser -G nginxgroup

# Create and set up directories with proper permissions
RUN mkdir -p /var/lib/nginx/tmp/client_body \
    /var/lib/nginx/tmp/proxy \
    /var/lib/nginx/tmp/fastcgi \
    /var/lib/nginx/tmp/uwsgi \
    /var/lib/nginx/tmp/scgi \
    /var/log/nginx \
    /run/nginx \
    && chown -R nginxuser:nginxgroup /var/lib/nginx /var/log/nginx /run/nginx

COPY nginx.conf /etc/nginx/nginx.conf

# Directory for static files
RUN mkdir -p /var/www/html && chown -R nginxuser:nginxgroup /var/www/html

# Port
EXPOSE 8080

USER nginxuser

CMD ["nginx", "-g", "daemon off;"]