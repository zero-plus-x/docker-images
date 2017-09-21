middleman
=========

Dockerized Ruby/Bundler/[Middleman](https://middlemanapp.com/) for generating static websites, based on [Alpine](https://docs.docker.com/samples/library/alpine/) Linux.

Usage
-----

While being at the root of your Middleman project (where you would normally run `middleman`), run any `middleman` command, for example:

```sh
# middleman build
docker run --rm -v $(pwd):/src zeroplusx/middleman build

# middleman server + open localhost URL in your browser when ready
docker run --rm -d -p 4567:4567 -v $(pwd):/src --name middleman-server zeroplusx/middleman server \
&& docker logs -f middleman-server | awk '/http:\/\/localhost/ {system("open http://localhost:4567")}'
```

When you are done, just press `CTRL+C` and it will close and remove the Docker container.

Maintainers
-----------

* Sebastian Mandrean (<sebastian@0x.se>)
