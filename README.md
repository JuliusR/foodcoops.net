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

If you just want to have a quick test from scratch then make sure to properly set up your database. An example to get some inspiration:

```shell
DB_CONTAINER=$(docker container ls -q -f name=foodcoopsnet_mariadb)
docker exec -it $DB_CONTAINER bash
mysql_secure_installation # and follow dialog...
mysql -u root -p
```

```sql
CREATE DATABASE foodsoft_test;
CREATE USER 'foodsoft' IDENTIFIED BY 'here you probably need your FOODSOFT_DB_PASSWORD set above';
GRANT ALL PRIVILEGES ON foodsoft_test.* TO 'foodsoft';
FLUSH PRIVILEGES;
exit
```
