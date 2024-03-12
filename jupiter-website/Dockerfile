# Base image
FROM amazonlinux:latest

# Install dependencies
RUN yum update -y && \
    yum install -y httpd && \
    yum search wget && \
    yum install wget -y && \
    yum install unzip -y

# Change directory
RUN cd /var/www/html

# Download webfiles
RUN wget https://github.com/azeezsalu/jupiter/archive/refs/heads/main.zip

# Unzip folder
RUN unzip main.zip

# Copy files into html directory
RUN cp -r jupiter-main/* /var/www/html/

# Remove unwanted folder
RUN rm -r jupiter-main main.zip

# Expose port 80 on the container
EXPOSE 80

# Set the default application that will start when the container starts
ENTRYPOINT ["/usr/sbin/httpd", "-D", "FOREGROUND"]