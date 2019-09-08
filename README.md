Fork of [parkervcp's image](https://github.com/parkervcp/pterodactyl-daemon-Dockerfile) with a version bump.

I might change more things in the future.

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
