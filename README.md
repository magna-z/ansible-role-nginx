nginx
---

Configure and run unprivileged Nginx as Docker container into systemd.service.


### Links:
- <https://nginx.org>
- <https://hub.docker.com/_/nginx>


### Requirements:
- **`sysctl net.ipv4.ip_unprivileged_port_start=0`** - Disable Linux privileged ports.


### Variables:
- **`nginx_docker_image`** *(type=string, default="nginx:latest")* - Docker image for using into systemd.service.

- **`nginx_docker_network`** *(type=string, default="bridge")* - Docker nerwork used as `docker run --network=...`.
- **`nginx_docker_publish_ports`** *(type=list, default=[])* - List of publish a container’s ports to the host as `docker run --publish=...`.

- **`nginx_uid`** & **`nginx_gid`** *(type=number, default=80)* - System user and group for run Nginx and store data as `docker run --user=...`.

- **`nginx_main_config`** *(type=string, mandatory)* - Multiline content for Nginx main config (`/etc/nginx/nginx.conf`).

- **`nginx_servers_config_files`** *(type=list, default=[])* - List of objects in format `{filename: ..., content: ...}`, where `filename` - filename in `/etc/nginx/conf.d/` and `content` - multiline string for `server {}` level config.
- **`nginx_ssl_files`** *(type=list, default=[])* - List of objects in format `{filename: ..., content: ...}`, where `filename` - filename in `/etc/nginx/ssl/` and `content` - multiline string with certificate (certificate chain) or private key, needed for HTTPS.
