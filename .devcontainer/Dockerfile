FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# Install Apache, PHP, and sudo
RUN apt-get update && \
    apt-get install -y apache2 php libapache2-mod-php sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Set up Apache
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf && \
    a2enmod rewrite

# Remove default content from /var/www/html
RUN rm -rf /var/www/html/*

# Copy the entire sample-webapp folder into /var/www
ADD ucw /var/www/html

# Create a symlink to /var/www/html in the workspace directory
RUN mkdir -p /workspace && \
    ln -s /var/www/html /workspace

WORKDIR /workspace

# Expose the web server port
EXPOSE 80

# Start Apache in the foreground
CMD ["apache2ctl", "-D", "FOREGROUND"]