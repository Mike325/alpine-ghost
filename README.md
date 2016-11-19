# Ghost on Alpine Linux

[![](https://badge.imagelayers.io/zzrot/alpine-ghost:latest.svg)](https://imagelayers.io/?images=zzrot/alpine-ghost:latest 'Get your own badge on imagelayers.io') [![Build Status](https://travis-ci.org/ZZROTDesign/alpine-ghost.svg?branch=master)](https://travis-ci.org/ZZROTDesign/alpine-ghost) [![Docker Pulls](https://img.shields.io/docker/pulls/zzrot/alpine-ghost.svg?maxAge=2592000)](https://hub.docker.com/r/zzrot/alpine-ghost/)

This is a [Docker](https://www.docker.com/) image for [Ghost](https://ghost.org). This image runs with a base of [Alpine-Linux](http://www.alpinelinux.org/) making it extremely small, secure and fast.

This image is also available on [Docker Hub](https://hub.docker.com/r/zzrot/alpine-ghost/).

## Usage
We recommend using our images in conjunction with [Docker-Compose](https://docs.docker.com/compose/). This allows for easier creation of containers with the proper volumes and ports enabled.

We have included an [example docker-compose](https://github.com/ZZROTDesign/alpine-ghost/blob/master/examples/docker-compose.example.yml) file to show how this image might be used both for development and production in a different project.

This image works out of the box with no volumes. It differs from the official Docker Ghost image by including a config.js file with some env variables defined.

1. DEV_DOMAIN = Is the domain that is reachable on your development machine. This is typically your docker-machine host ip
2. PROD_DOMAIN = When running this image in production (NODE_ENV=production), this is the domain that is used.

This image also runs with containers. It will accept a volume from your ghost content folder, as well as a custom config.js file. These must point to /var/lib/ghost/ - See the [example docker-compose](https://github.com/ZZROTDesign/alpine-ghost/blob/master/examples/docker-compose.example.yml) for specification.

### Available ENV Variables

- DEV_DOMAIN: URL for Ghost Blog running in Development
- DEV_FORCE_ADMIN_SSL: Force SSL (secure HTTP or https) for the admin panel in Development

- PROD_DOMAIN: URL for Ghost Blog running in Production
- PROD_FORCE_ADMIN_SSL: Force SSL (secure HTTP or https) for the admin panel in Production

- USE_PROD_ENV: Copy the values of the Production variables to the Development variables (default to false)

- PRELOAD_HEADERS: Number of headers to be preloaded (default to 25) 

#### Mail ENV VARIABLES

- DEV_MAIL_TRANSPORT: Type of Transport used for Development Email
- DEV_MAIL_SERVICE: The Service by which email will be sent in Development
- DEV_MAIL_HOST: Hostname of the SMTP server (defaults to "localhost", not needed with DEV_MAIL_SERVICE)
- DEV_MAIL_NAME: The name of the client server (defaults to machine name)
- DEV_MAIL_USER: Username for the Development email service
- DEV_MAIL_PASS: Password for the Development email service
- DEV_MAIL_FROM: Address which the Development email will be sent from
- DEV_MAIL_SECURE_CONNECTION: Use SSL (default is false, not needed with DEV_MAIL_SERVICE)
- DEV_MAIL_PORT: Port of the SMTP server (defaults to 25, not needed with DEV_MAIL_SERVICE)
- DEV_MAIL_IGNORE_TLS: Ignore server support for STARTTLS (defaults to false)
- DEV_MAIL_DEBUG: Output client and server messages to console

- PROD_MAIL_TRANSPORT: Type of Transport used for Production Email
- PROD_MAIL_SERVICE: The Service by which email will be sent in Production
- PROD_MAIL_HOST: Hostname of the SMTP server (defaults to "localhost", not needed with PROD_MAIL_SERVICE)
- PROD_MAIL_NAME: The name of the client server (defaults to machine name)
- PROD_MAIL_USER: Username for the Production email service
- PROD_MAIL_PASS: Password for the Production email service
- PROD_MAIL_FROM: Address which the Production email will be sent from
- PROD_MAIL_SECURE_CONNECTION: Use SSL (default is false, not needed with PROD_MAIL_SERVICE)
- PROD_MAIL_PORT: Port of the SMTP server (defaults to 25, not needed with PROD_MAIL_SERVICE)
- PROD_MAIL_IGNORE_TLS: Ignore server support for STARTTLS (defaults to false)
- PROD_MAIL_DEBUG: Output client and server messages to console

#### Database ENV VARIABLES

- DEV_DB_CLIENT: Client of the Development database; sqlite3 (default) or mysql
- DEV_DB_HOST: Hostname of the Development database server (not needed with sqlite3)
- DEV_DB_USER: Username for the Development database (default root, not needed with sqlite3)
- DEV_DB_PASS: Password for the Development database (default "blank", not needed with sqlite3)
- DEV_DB_NAME: Name of the Development database (default ghost, not needed with sqlite3)
- DEV_DB_PORT: Port of the Development database's host (default 3306 for mysql, not needed with sqlite3)

- PROD_DB_CLIENT: Client of the Production database; sqlite3 (default) or mysql
- PROD_DB_HOST: Hostname of the Production database server (not needed with sqlite3)
- PROD_DB_USER: Username for the Production database (default root, not needed with sqlite3)
- PROD_DB_PASS: Password for the Production database (default "blank", not needed with sqlite3)
- PROD_DB_NAME: Name of the Production database (default ghost, not needed with sqlite3)
- PROD_DB_PORT: Port of the Production database's host (default 3306 for mysql, not needed with sqlite3)

## Getting Started

To run this container with the predefined defaults:

    docker run -p 2368:2368 zzrot/alpine-ghost

Now the Ghost container will be available at your.dockermachine.ip:2368.

See the example compose file for specification of including the ENV variables as well as the volumes.

### Volumes

This image has one volume that can be utilized. By connecting a folder with:

     /var/lib/ghost/

You can not only keep your data persistent, but also upload a custom config.js file. In order to do this connect your volume like this:

     /your/contentfolder:/var/lib/ghost/


## Contributing to Alpine-Ghost

### Team members

* [Sean Kilgarriff](https://github.com/Skilgarriff) sean@zzrot.com T: [@seankilgarriff](https://twitter.com/SeanKilgarriff)
* [Killian Brackey](https://github.com/killianbrackey) killian@zzrot.com T: [@kmbrackey](https://twitter.com/kmbrackey)

Don't hesitate to get in contact with either one of us with problems, questions, etc.


### Adding new features

* Fork it!
* Create your feature branch: git checkout -b my-new-feature
* Commit your changes: git commit -am 'Add some feature'
* Push to the branch: git push origin my-new-feature
* Submit a pull request :D


Don’t get discouraged! We estimate that the response time from the
maintainers is around: 24 hours.

## Reporting Security Issues

If you discover a security issue in this Docker image, please report it by sending an email to docker@zzrot.com

This will allow us to assess the risk, and make a fix available before we add a bug report to the GitHub repository.

Thanks for helping make this image safe for everyone!


## License

The code is available under the [MIT License](https://github.com/ZZROTDesign/alpine-ghost/LICENSE).
