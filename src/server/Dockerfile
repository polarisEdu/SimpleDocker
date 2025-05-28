FROM nginx:latest

# Install necessary packages
RUN apt-get update && \
    apt-get install -y gcc spawn-fcgi libfcgi-dev

# Copy Nginx configuration
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf

# Copy and compile the FastCGI server
COPY ./server.c /usr/local/bin/
RUN gcc /usr/local/bin/server.c -o /usr/local/bin/server -lfcgi

# Start services
CMD service nginx start && \
    spawn-fcgi -p 8080 /usr/local/bin/server && \
    tail -f /dev/null
