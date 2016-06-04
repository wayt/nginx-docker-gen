# nginx-docker-gen

This is a basic docker-gen template for nginx load balancing a docker swarm cluster.

This aim to provide a strong load balancer configuration, outside docker.

Based on @jwilder work on https://github.com/jwilder/nginx-proxy

Only support http ATM.

## Usage

Tested on debian 8, nginx 1.6.2, docker-gen 0.7.1, swarm 1.2.3, docker 1.11.2

Run it:

```
docker-gen --watch -only-published --notify "nginx -s reload" --endpoint tcp://<swarm-ip>:<swarm-port> nginx.tmpl /etc/nginx/sites-enabled/default
```

Then start your containers using labels:
* virtual host: `labels=lb.vhost=your-vhost.com`
* container port: `labels.lb.servicePort=1234`, default 80

Container port MUST be published (randomly is better).

See `docker-compose.yml` for a demo.


## Contributing

This is a POC, feel free to comment.
