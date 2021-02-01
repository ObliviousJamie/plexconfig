# Containerised Plex media server 

This repo contains a docker-compose file to build a variety of services that are useful for running a media center.

## Services

- [Plex Media Server](https://github.com/plexinc/pms-docker)

Plex Media Server is a server for your video, music and photo collections. You can stream to a variety of client devices.

- [Sonarr](https://github.com/Sonarr/Sonarr)

Sonarr is a PVR for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them. It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available.

- [Radarr](https://github.com/Radarr/Radarr)

Radarr is a movie collection manager for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new movies and will interface with clients and indexers to grab, sort, and rename them. It can also be configured to automatically upgrade the quality of existing files in the library when a better quality format becomes available.

- [Bazarr](https://github.com/morpheus65535/bazarr)

Bazarr is a companion application to Sonarr and Radarr. It manages and downloads subtitles based on your requirements. You define your preferences by TV show or movie and Bazarr takes care of everything for you.

- [Jackett](https://github.com/Jackett/Jackett)

Jackett works as a proxy server: it translates queries from apps (Sonarr, Radarr, SickRage, CouchPotato, Mylar, Lidarr, DuckieTV, qBittorrent, Nefarious etc.) into tracker-site-specific http queries, parses the html response, then sends results back to the requesting software. This allows for getting recent uploads (like RSS) and performing searches. Jackett is a single repository of maintained indexer scraping & translation logic - removing the burden from other apps.

- [Transmission/OpenVPN](https://github.com/haugene/docker-transmission-openvpn)

This container contains OpenVPN and Transmission with a configuration where Transmission is running only when OpenVPN has an active tunnel. It has built in support for many popular VPN providers to make the setup easier.

## Setup

Set environment variables or create a .env file in the same directory as the docker-compose.yml file.

Example .env file (see [Transmission/OpenVPN](https://github.com/haugene/docker-transmission-openvpn) for VPN settings):
```
# General
MOUNT_POINT=/mnt/d/Plex
# VPN
VPN_PROVIDER=PIA
VPN_COUNTRY=netherlands,switzerland,romania,spain
VPN_USER=username
VPN_PASSWORD=password
# Plex
PLEX_IP=http://192.168.X.X:32400/
PLEX_CLAIM=claimhere
PLEX_HOSTNAME=DockerPlexServer
```

## FAQ

### Confirm VPN connection
```
docker exec -it radarr curl ipinfo.io/json
```