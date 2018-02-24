# easy-traefik

Make usage of [Traefik](https://github.com/containous/traefik) even simpler.

Traefik is a wonderful tool to simplify exposure of multiple web services through a unified http/https interface. However we are lazy guys and were too lazy to read through the comprehensive documentation ;-)

This project is aimed at simplifying our use cases:

1. Expose multiple services hosted on our home network through a single https server hosted on a Raspberry Pi

2. Detect and monitor service downtime and redirect traffic accordingly.

### Configuration

The project is configured through a `traefik.toml` file which is based upon the sample file in the Traefik sources. Use it at your own risk!

For the moment the address and port of the redirected service is hardcoded - see [open issues](https://github.com/gmacario/easy-traefik/issues).

### Running

```
docker run -d -p 8080:8080 -p 80:80 \
    -v $PWD/traefik.toml:/etc/traefik/traefik.toml \
    -v /var/run/docker.sock:/var/run/docker.sock \
    traefik
```

You may inspect logs with the usual `docker logs -f <container_id>`


Have fun!
