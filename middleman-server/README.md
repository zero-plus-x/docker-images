middleman-server
================

Server container for Ruby/Bundler/[Middleman](https://middlemanapp.com/) static websites, based on [Alpine](https://docs.docker.com/samples/library/alpine/).

Usage
-----

While being at the root of your Middleman project (where you would normally run `middleman`), run this beautiful oneliner:

```sh
docker run --rm -d -p 4567:4567 -v $(pwd):/src --name middleman-server zeroplusx/middleman-server \
&& docker logs -f middleman-server | awk '/http:\/\/localhost/ {system("open http://localhost:4567")}'
```

It will automatically open `http://localhost:4567` in your browser when `middleman` is ready for serving.

Maintainers
-----------

* Sebastian Mandrean (<sebastian@0x.se>)
