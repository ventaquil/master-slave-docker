FROM nginx
RUN apt-get update && apt-get install -y curl iputils-ping socat vim wget
RUN apt-get install -y ssh
COPY ./conf.d /etc/nginx/conf.d
COPY ./entrypoint /entrypoint
COPY ./html /usr/share/nginx/html
EXPOSE 2222
CMD ["/entrypoint"]

