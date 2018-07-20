FROM nginx
RUN apt-get update && apt-get install -y curl iputils-ping vim wget
RUN apt-get install -y socat
COPY ./conf.d /etc/nginx/conf.d
COPY ./html /usr/share/nginx/html

