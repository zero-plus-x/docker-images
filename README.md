0+X Docker Images
=================

A variety of different docker images curated by 0+X, mainly for internal work.

Pre-requisites
--------------

* [Docker](https://docs.docker.com/engine/installation/)

Images
------

| Name                                           | Description                                                 |
|------------------------------------------------|-------------------------------------------------------------|
| [zeroplusx/middleman-build](middleman-build)   | Build container for Ruby/Bundler/Middleman static websites  |
| [zeroplusx/middleman-server](middleman-server) | Server container for Ruby/Bundler/Middleman static websites |

Snippets
--------

Useful snippets for cleanups etc.

| **Action**                                                       | **Snippet** |
|------------------------------------------------------------------|-------------|
| Stop all containers                                              | docker stop \$(docker ps -a -q) |
| Remove all containers                                            | docker rm \$(docker ps -a -q) |
| Remove all images                                                | docker rmi \$(docker images -q) |
| Remove orphaned volumes                                          | docker volume rm \$(docker volume ls -qf dangling=true) |
| Remove exited containers                                         | docker rm -v \$(docker ps -a -q -f status=exited) |
| Stop & Remove all containers with base image name \<image_name\> | docker rm \$(docker stop \$(docker ps -a -q --filter ancestor=\<image_name\>)) |
| Remove dangling images                                           | docker rmi \$(docker images -f "dangling=true" -q) |
| Cleanup Volumes                                                  | docker run -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker:/var/lib/docker --rm martin/docker-cleanup-volumes |

Maintainers
-----------

* Sebastian Mandrean (<sebastian@0x.se>)
