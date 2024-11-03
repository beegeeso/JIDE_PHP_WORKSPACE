FROM ubuntu:22.04

# Set environment variable to avoid prompts
ENV DEBIAN_FRONTEND=noninteractive

# Install Apache, PHP, and other dependencies
RUN apt-get update && \
    apt-get install -y apache2 php libapache2-mod-php tzdata && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Reset the DEBIAN_FRONTEND variable to default
ENV DEBIAN_FRONTEND=

# Set up Apache
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf && \
    a2enmod rewrite

# Create a symlink to /var/www/html in the workspace directory
RUN mkdir -p /workspace && \
    ln -s /var/www/html /workspace/html

WORKDIR /workspace

# Expose the web server port
EXPOSE 80

# Start Apache in the foreground
CMD ["apache2ctl", "-D", "FOREGROUND"]
