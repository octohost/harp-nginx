harp-nginx
==================

You don't need to use node to serve a harp site - you can just compile the files and use anything - `harp compile`

This is a container that has node and harp available, to compile and install the static site, that nginx serves.

You can use our container: `docker pull octohost/harp-nginx`

Or you can build your own:

```
docker build -t your-name-here/harp-nginx .
docker push your-name-here/harp-nginx
```

After this - just add this Dockerfile to your Harp repo:

```
FROM octohost/harp-nginx

WORKDIR /srv/www

ADD . /srv/www/
RUN harp compile

EXPOSE 80

CMD nginx
```

Push it to your docker server - and your server will use 4-6MB of RAM instead of 60MB.
