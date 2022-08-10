# Lumeo Gateway Balena Block

> Currently only supports Jetson Xavier NX

## Setup your Fleet
First, setup the following Fleet-wide or Device variables in Balena cloud:
```
LUMEO_APP_ID=<your Lumeo workspace app id>
LUMEO_API_KEY=<api key for your Lumeo workspace>
```
This will enable containers that you push to your fleet to automatically
register in this workspace.

## Usage instructions
Include this snippet in your docker-compose.yml file:
```
volumes:
    lumeo-data:
services:
    lumeo:
        image: bh.cr/lumeo/lumeo-gateway-block 
        network_mode: 'host'
        privileged: true
        volumes:
            - 'lumeo-data:/var/lib/lumeo'    
        labels:
            io.balena.features.balena-socket: '1'
```

To pin to a specific [version](CHANGELOG.md) of this block use:
```
volumes:
    lumeo-data:
lumeo:
    image: bh.cr/lumeo/lumeo-gateway-block/<version> 
    network_mode: 'host'
    privileged: true
    volumes:
          - 'lumeo-data:/var/lib/lumeo'    
    labels:
          io.balena.features.balena-socket: '1'
```

# Additional Info
When you use this block in your application, be sure to log into your hardware device and set max perf mode : 

```.bash
$ balena ssh <device-uuid>

# NVP Mode 8 sets Jetson NX to 20W, 6 core (max perf).
$ nvpmodel -m 8
```
