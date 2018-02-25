# Running NextCloud in a Docker container

Sample command for running [NextCloud](https://nextcloud.com/) in a Docker container using an external SQLite database

```
docker run -d -p 8088:80 \
  -v $PWD/nextcloud:/var/www/html \
  -e SQLITE_DATABASE=/var/www/html/nextcloud.sqlite \
  nextcloud
```

NextCloud will listen at <http://localhost:8088> using an Apache webserver.

Contributor: [@xrmx](https://github.com/xrmx)

Reference: [NextCloud documentation](https://docs.nextcloud.com/)

<!-- EOF -->
