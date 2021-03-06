# Heatmiser-for-home-assistant
Heatmiser Neo-Hub / Neostat / Neostat-e support for home-assistant.io

This is a work in progress for adding Heatmiser Neo-hub support to Home Assistant (https://home-assistant.io/), I maintain this as a weekend project only so don't expect fast updates but feel free to raise issues as needed.

Installation:

For Hass.io:
Install and configure SSH server from the "Add-on store". Once you have shell run the following:
```
cd /config/
mkdir -p custom_components/heatmiserneo/
cd /config/custom_components/heatmiserneo/
wget https://raw.githubusercontent.com/MindrustUK/Heatmiser-for-home-assistant/master/climate.py
```

For Manual / Custom installations:
Change directory to config location then run the following:
```
mkdir -p custom_components/heatmiserneo/
cd custom_components/heatmiserneo/
wget https://raw.githubusercontent.com/MindrustUK/Heatmiser-for-home-assistant/master/climate.py
```
For both above scenarios then complete configuration as follows:

General Configuration:

[Authors note: Add notes about how to find your heatmiser neohub on your network (Nmap, checking your routers DHCP table, ARP etc).]

Suggestions from Haakon Storm Heen, Use namp on your local network range:

```nmap -Pn -p4242 -oG - 192.168.1.0/24 | grep 4242 | grep -i open```

As per example_configuration.yaml, add the following to the configuration.yaml in your /config directory.

```
climate:
  - platform: heatmiserneo
    host: <Insert IP Address / Hostname>
    port: 4242
```

(Optional) Logging Configuration:

If debugging is required (submitting bug reports etc.) logger verbosity can be adjusted as follows:

```
logger:
  default: debug
  logs:
    homeassistant.components.climate.heatmiserneo: debug
```
