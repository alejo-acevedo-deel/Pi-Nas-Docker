# PI-NAS-DOCKER

Here, I have some stuff that I use to develope my PI-NAS Server over Docker

## Publish local domains

I used some local domain to could reach all my service easily. For these reason I have used avahi-utils plus haproxy

1. Install avahi-utils `sudo apt-get install avahi-utils`
2. Move avahi-aliase@.service to /etc/systemd/system `sudo cp avahi-aliase@.service /etc/systemd/system/avahi-aliase@.service`
3. Publish all required domains `sudo systemctl enable --now avahi-alias@subdomain.domain.local.service`

## Zerotier

To reach my network from outside of my house I use [zerotier](zerotier.com) and ztdns to get some internal friendly url

1. Install zerotier
2. Join zerotier `sudo zerotier-cli join {network-id}`
3. Config ztdns/.ztdns.toml with your API token and your managed ip

## Docker

To deploy all service at once I use docker and docker-compose

1. Deploy `docker-compose up -d`

## Transmission

Torrent client to download anything. Default user and password is `admin` `admin` PLEASE CHANGE IT at `./media/transmission/settings.json`

## Jackett

Jackett is an indexer to obtain some info about movies and series

1. Go to [jackett-page](http://jackett.pi-nas.local)
2. Choose some indexers.

## Sonarr, Radarr and Bazarr

This three make your life easier and happier

1. Go to [sonarr-page](http://sonarr.pi-nas.local), [radarr-page](http://radarr.pi-nas.local), [bazarr-page](http://bazarr.pi-nas.local)
2. Configure it to contact jackett. They are at the same docker network so, you can use just `jackett` like url

## Plex

The choosen media server

1. First time you have to make a port-fowarding `ssh -L 32400:pi-nas.local:32400 pi@pi-nas.local`
2. Claim server with your plex account

