# Private Pad - [Back](/index.md)
## Motivation
The advent of several critical vulnerabilities along with coming to understand the depth of windows telemetry and its lack of security has motivated me to shift towards a more secure and private setup.

[Top](#private-pad)

## Current Features
* Soft Disable of the Intel ME: The intel management engine is one of many pieces of remote control firmware that come pre-packaged into nearly every off the shelf bios. The management engine, having a higher authority than the kernal, would be a significantly high value target for potential malware. By soft disabling this unneeded feature, this removes the option of a malicious driver or kernal update leading to management engine infection which to my knowledge would require the bios to be reflashed to be resolved. This was accomplished via the [1vyrain](https://github.com/n4ru/1vyrain) exploit chain to install an unlocked version of the bios on my device, thus enabling the management engine to be turned off in the bios.

* Hardened GNU/Linux Distro: I transitioned from windows for a variety of reasons, chiefly among them being system control and security. The linux distro Void is one of the more hardened distros out there, without verging into the territory of requiring significant work to enable core system functionality (as is the case with alpine or gentoo). Everything installed into void is containerized, thus allowing for compartmentalization and removing some of the risk with applications accessing memory that is not theirs to access.

* MAC-Address Spoofing: Configured an automated script to spoof the MAC-Address every day, thus preventing a network from keeping a multi-day log of my traffic and building a profile of my habits.

* Mulvad VPN: VPNs shift trust from the ISP to the VPN provider. Thus when on untrusted networks, such as airport or hotel networks, using a VPN will prevent them from snooping on your traffic without significant effort. Additionally Mulvad is the only VPN provider beyond potentially ProtonVPN that has passed the sniff test.

[Top](#private-pad)

## Planned Features
* [I2p Connectivity](https://i2p.net/en/): The internet to peer projects is one of the best out there for web traffic privacy. The traffic is proxied between several users in a similar, but more distributed manner, to tor. Additionaly the encrypted traffic is bundled with other users (this is called a clove, like cloves of garlic) in order to obfuscate who is doing what and help prevent fingerprinting. The end goal would to be to potentially enable communication between my devices over i2p, possibly as fully fleshed out messaging service but this is all in the pre-planning phase as of now.

* 3rd Party BIOS: Installing a 3rd party bios is one other way to disable the intel management engine on a more permanent basis. This would also allow total control over my firmware and would give me experience flashing the bios externally. 

[Top](#private-pad)
