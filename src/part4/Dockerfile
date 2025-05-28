# Use the official Nginx image as the base image
FROM nginx:latest

# Install required packages
RUN apt-get update && \
    apt-get install -y gcc spawn-fcgi libfcgi-dev && \
    apt-get clean

# Copy configuration and source files
COPY ../nginx/nginx.conf /etc/nginx/nginx.conf
COPY ../nginx/fastcgi_params /etc/nginx/fastcgi_params
COPY ../server/server.c /usr/local/bin/server.c

# Compile the server
RUN gcc /usr/local/bin/server.c -o /usr/local/bin/server_exec -l fcgi

# Start nginx and the FastCGI server
CMD ["sh", "-c", "spawn-fcgi -p 8080 /usr/local/bin/server_exec && nginx -g 'daemon off;'"]
