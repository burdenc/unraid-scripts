# Check VPN Health

Script to periodically check a docker container's internet connection and restart if unhealthy.

This could probably be done through docker health checks, but this is a quick and dirty script to achieve it.

I mainly use this to reset my VPN docker if it for some reason loses connection.

## Setup

Change `VPN_CONTAINER` to the name of the docker container you want to check for internet connection.

Change `CONTAINERS_TO_RESTART` to the name of docker containers you want to restart if `VPN_CONTAINER` is unhealthy. Usually for any containers that route their internet through the VPN container.

