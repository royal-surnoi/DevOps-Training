# Use Ubuntu 20.04 as the base image
FROM ubuntu:20.04

# Update package lists and install necessary packages
RUN apt-get update \
    && apt-get install -y nginx git \
    && rm -rf /var/lib/apt/lists/*

# Copy default Nginx configuration file to overwrite
COPY nginx-default /etc/nginx/sites-available/default

# Create a directory for Nginx to hold the cloned code
RUN mkdir -p /var/www/html/*

# Clone the Git repository into the Nginx root directory
RUN git clone https://github.com/yourusername/yourrepository.git /var/www/html/myapp

# Expose port 80 for Nginx
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
