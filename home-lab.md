# My Home Lab - [Back](/index.md)
### Sections
* [Network Configuration](#network-configuration)
* [Implemented Services](#implemented-services)
* [Planned Services](#planned-services)

## Network Configuration
* Router: Custom built router running the OPNsense operating system. This os was chosen over openwrt, pfsense or a closed source option for its stateful firewall, comaptibility with x86_64 processors, thus enabling upgrades for futer planned network expansions to 10Gb fiber, and the free and opensource nature that forgos the requirement of an account or recuring subscription.

* Switches: Currently in use is a Netgear GS305E 5-port managed switch and a Netgear GS308 8-port umanaged switch. These where chosen primarily for their cost, avilibilty, and, in the case of the GS305E, features.

* Acess Points: The network contains one access point, a Ubiquity U6 Pro, for all VLANs as the physical area of the network is well within its range and one AP supports more then enough VLANs.

* VLANs: There is currently guest, home, and service VLANs within the network. The guest VLAN will be completely untrusted and only allow traffic to the wider internet. The home VLAN will allow connection to the services network and to the wider internet. All traffic leaving the home VLAN to the wider internet will be routed through mulvad to improve the OpSec of the private portion of the network. The services VLAN will not be able to connect to the wider internet with very few exceptions such as netbird or tailscale.

[Top](#my-home-lab)

## Implemented Services

[Top](#my-home-lab)

## Planned Services
* Jellyfin Media Server: A home video server that would allow me to stream media from any device within my network.
  
* Authentik SSO: A single sign-on provider that would simplify and streamline any authentication for self hosted services.
  
* NAS Server: A central location for file storage for devices across the network.
  
* DNS Filtering: Likely going to leverage PI-hole to enable ad-blocking for devices that are unable to have client side ad-blockers.
  
* Remote Client Access: Utilizing Netbird I will enable remote clients to have access to the services hosted on the network.
  
[Top](#my-home-lab)
