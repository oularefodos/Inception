# FROM alpine:3.17


# RUN apk update && apk add curl

# RUN curl -L https://github.com/portainer/portainer/releases/download/2.16.2/portainer-2.16.2-linux-amd64.tar.gz -o /tmp/portainer-2.16.2-linux-amd64.tar.gz --silent
    
# RUN tar -xvf /tmp/portainer-2.16.2-linux-amd64.tar.gz -C &&/
#     chmod +x /portainer/portainer

# EXPOSE 9000

# CMD ["/portainer/portainer"]

FROM debian:buster

RUN apt update && apt upgrade -y && apt install -y curl

RUN curl -L https://github.com/portainer/portainer/releases/download/2.16.2/portainer-2.16.2-linux-amd64.tar.gz -o /tmp/portainer-2.16.2-linux-amd64.tar.gz --silent 

RUN tar -xvf /tmp/portainer-2.16.2-linux-amd64.tar.gz -C /

# RUN mv /tmp/portainer/portainer /usr/bin/portainer

RUN chmod +x /portainer/portainer

ENTRYPOINT [ "/portainer/portainer" ]