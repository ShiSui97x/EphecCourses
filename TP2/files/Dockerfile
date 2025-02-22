FROM nginx
RUN apt update && apt install -y nano iproute2 iputils-ping && apt clean
COPY html/index.html /usr/share/nginx/html/index.html