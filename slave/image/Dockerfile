FROM nginx
RUN apt-get update && apt-get install -y curl iputils-ping socat vim wget
RUN apt-get install -y openssh-server && mkdir /var/run/sshd
COPY ./conf.d /etc/nginx/conf.d
COPY ./entrypoint /entrypoint
COPY ./html /usr/share/nginx/html
RUN useradd -m test && echo "test:test" | chpasswd
CMD ["/entrypoint"]

