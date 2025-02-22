FROM httpd:latest
RUN apt update && apt install -y nano iproute2 iputils-ping && apt clean

COPY index.html /usr/local/apache2/htdocs