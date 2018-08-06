# Docker isolated container

Simple example how to isolate container from the Internet.

There are two containers: `master` - which is proxy - and `slave` - which has not Internet connection.

## Preparation

Start containers by executing

    $ docker-compose up

You can use `-d` flag to start this process in background. More information are available in [Docker documentation](https://docs.docker.com/compose/reference/up/).

At first images should be automatically build.

After this process you can check that two containers are up

    $ docker-compose ps

Then you can open your browser and enter `localhost`. You should get `Welcome to master-nginx!`.

When you enter `localhost/slave` you should get `Welcome to slave-nginx!`.

## Testing Internet connection

Copy code below into your terminal

    $ docker-compose exec master ping -c4 8.8.8.8
    
You should get that `0% packet loss`. Your master container has Internet connection. In any other cause you should check your host machine Internet connection.

Next step is to check `slave` container

    $ docker-compose exec slave ping -c4 8.8.8.8

In response you should get `100% packet loss`. You can choose address whatever you want. Response should be same.

## SSH trough socket

To connect with your container using SSH use `2222` port and `test` account (default password is `test`)

    $ ssh -p 2222 test@localhost

You have two directional connection but you still cannot ping Google Public DNS or any site in the Internet.

## Next steps

You can prepare more complicated example - add domains, subdomains and some scripts.

You can add two slaves - one with [NGINX](https://www.nginx.com/) and other one with [HTTPD](https://httpd.apache.org/).

Do whatever you want.
