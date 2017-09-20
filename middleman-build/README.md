middleman-build
===============

Build container for Ruby/Bundler/[Middleman](https://middlemanapp.com/) static websites, based on [Alpine](https://docs.docker.com/samples/library/alpine/).

Usage
-----

While being at the root of your Middleman project (where you would normally run `middleman build`), run:

```sh
docker run --rm -v $(pwd):/src zeroplusx/middleman-build
```

Maintainers
-----------

* Sebastian Mandrean (<sebastian@0x.se>)
