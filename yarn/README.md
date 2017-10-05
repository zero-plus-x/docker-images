yarn
=========
node/npm/[Yarn](https://yarnpkg.com/) Docker image for installing dependencies & building nodejs applications, based on [Alpine](https://docs.docker.com/samples/library/alpine/) Linux.

Usage
-----
While being at the root of your node project (where you would normally run `node`, `npm` or `yarn`), run any `yarn` command, for example:

```sh
# yarn install
docker run --rm -v $(pwd):/app zeroplusx/yarn

# custom commands like yarn build/start/prod etc.
docker run --rm -v $(pwd):/app zeroplusx/yarn build
docker run --rm -v $(pwd):/app zeroplusx/yarn start
docker run --rm -v $(pwd):/app zeroplusx/yarn prod
```

When you are done, just press `CTRL+C` and it will close and remove the Docker container.

Maintainers
-----------
* Sebastian Mandrean (<sebastian@0x.se>)
