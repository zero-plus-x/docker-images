static-nginx
============
Base image for static website builds to be served using [nginx](https://hub.docker.com/_/nginx/).

Usage
-----
In it's most simple form, you could run for example the following from your website index root:

```sh
docker run -v $(pwd):/usr/share/nginx/html -p 8080:80 zeroplusx/static-nginx
```
Then just open http://localhost:8080 in your browser.

Nginx also listens to container port 8080, for scenarios where that might be needed:
```sh
docker run -v $(pwd):/usr/share/nginx/html -p 8080:8080 zeroplusx/static-nginx
```

More likely is that `zeroplusx/static-nginx` will be used as a base image for static website builds. Using the default `nginx.conf`, you should add your files to `/usr/share/nginx/html`:

```dockerfile
FROM zeroplusx/static-nginx

COPY public/ /usr/share/nginx/html
```

Maintainers
-----------
* Sebastian Mandrean (<sebastian@0x.se>)
