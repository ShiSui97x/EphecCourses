FROM sameersbn/bind:latest

RUN apt update && apt install -y nano

COPY named.conf.options /etc/bind/named.conf.options

# Exposer les ports DNS
EXPOSE 53/tcp
EXPOSE 53/udp

CMD ["/bin/bash", "-c", "/usr/sbin/named -g -c /etc/bind/named.conf"]
