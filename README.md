# easy-traefik

Make usage of [Traefik](https://traefik.io/) even simpler.

This project was started by [@gmacario](https://github.com/gmacario) and [@xrmx](https://github.com/xrmx) during the [8th Open Source Saturday Torino](https://www.meetup.com/it-IT/open-source-saturday-torino/events/247352073/) and addresses the following use cases:

1. Expose multiple services hosted on our home network through a single https server hosted on a Raspberry Pi

2. Detect and monitor service downtime and redirect traffic accordingly.

Traefix is a wonderful tool which makes it easy to expose multiple web services through a unified http/https interface. Everything is done with a proper configuration and/or interacting with its REST APIs, which you may learn by reading through its comprehensive [documentation](https://docs.traefik.io/).

Alternatively, if you are a lazy guy like we are, just run this project and you are done ;-)

### Configuration

The project is configured through a `traefik.toml` file which is based upon the sample file in the Traefik sources. Use it at your own risk!

For the moment the IP address and port of the redirected service are hardcoded - see [open issues](https://github.com/gmacario/easy-traefik/issues).

### Running

```bash
cd ~/github/gmacario/easy-traefik
touch acme.json && chmod 600 acme.json
docker run -d --restart always \
    -p 8080:8080 -p 80:80 -p 443:443 \
    -v $PWD/acme.json:/acme.json \
    -v $PWD/traefik.toml:/etc/traefik/traefik.toml \
    -v /var/run/docker.sock:/var/run/docker.sock \
    traefik
```

You may inspect logs with the usual `docker logs -f <container_id>`

Have fun!
