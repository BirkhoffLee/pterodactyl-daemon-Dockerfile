Fork of [parkervcp's image](https://github.com/parkervcp/pterodactyl-daemon-Dockerfile) with a version bump.

This is made compatiable with Traefik and Cloudflare CDN. Set the SSL port to 443 in the configurations, reverse proxy ON.

# Fetch daemon config automatically
```
$ docker-compose run daemon npm run configure -- --panel-url <panel_url> --token <panel_token>
```

# Error: Pool overlaps with other one on this address space
https://pterodactyl.io/daemon/configuration.html#custom-network-interfaces
```
"docker": {
    "socket": "/var/run/docker.sock",
    "autoupdate_images": true,
    "network": {
      "name": "pterodactyl_nw",
      "interfaces": {
        "v4": {
          "subnet": "172.254.0.0/16",
          "gateway": "172.254.0.1"
        }
      }
    },
    "interface": "172.254.0.1"
},
```
and run `systemctl restart docker`

# Permissions
If you happen to use OVH as well, the main storage is mounted to `/home`, so we're gonna put `daemon-data` in it.  
So run the following as root:
```
$ chmod -R 0761 /home/daemon-data
```
So other Linux users can't read the server files, which improves security.
