FROM ubuntu

RUN apt update -y && apt install ssh -y && apt install sudo -y

RUN adduser ansible

RUN echo "ansible:123" | chpasswd

RUN usermod -aG sudo ansible

ENTRYPOINT service ssh restart && bash

# 172.17.0.2

#on my machine:
# /home/samy/.ssh/key   #private key
# /home/samy/.ssh/key.pub   #public key