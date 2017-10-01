Foodcoops.net deployment demo
=============================

You need to create a certificate for your setup before you can start. The certificate must be a single file containing the blocks `-----BEGIN PRIVATE KEY-----` and `-----BEGIN CERTIFICATE-----`. For testing purpose only you can add it via `COPY` in `haproxy/Dockerfile` or you mount it via a volume in the `docker-compose.yml`. Check out the comments in the files.

To get it running you need to provide the private information via environment variables to `docker-compose`. Here is an example to build and start the project:

```shell
export FOODSOFT_DB_PASSWORD=foodsoft
export FOODSOFT_SECRET_KEY_BASE=secret
export MYSQL_ROOT_PASSWORD=mysql
docker-compose build --pull
docker-compose up -d
```
