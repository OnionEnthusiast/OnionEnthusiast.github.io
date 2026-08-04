# Private Pad - [Back](/../index.md)
## Motivation
The recent emergence of significant security vulnerabilities within major software ecosystems has prompted me to critically reassess my digital environment. Furthermore, having gained clarity regarding the extensive data collection practices inherent in standard Windows telemetry and their associated privacy risks, I have decided to transition toward a hardened infrastructure that prioritizes both robustness and personal sovereignty over sensitive information.

[Top](#private-pad)

## Current Features
* Soft Disable of the Intel ME: To significantly harden my system against firmware vulnerabilities, I have implemented a soft disable of the Intel Management Engine (IME). The IME, being a pre-packaged remote control module embedded within nearly all off the shelf BIOS/UEFI configurations on Intel devices, operates at privilege levels exceeding those of the standard operating system kernel and serves as a significant high-value target for sophisticated malware attacks. Disabling this unnecessary system via software configuration, effectively removes the attack vector where malicious drivers or kernel updates could lead to an engine infection. Such a breach would typically necessitate a full hardware re-flash to resolve. This modification was successfully accomplished by leveraging the [1vyrain](https://github.com/n4ru/1vyrain) exploit chain to install a modified version of the stock Lenovo firmware on my device, thereby unlocking advanced settings and enabling direct control over management engine functionality within the interface.

* Hardened GNU/Linux Distro: In pursuit of enhanced autonomy and a robust security posture, I have transitioned away from Windows in favor of Void Linux. This distribution was selected specifically to balance hardening protocols with operational usability; unlike minimalistic environments such as Alpine or Gentoo, which often demand intensive manual configuration for basic system functions, Void provides these features out-of-the-box without compromising functionality. To further mitigate risk within this architecture, all installed applications are deployed through containerization technology. This method ensures strict process isolation and compartmentalization, significantly reducing the security exposure associated with potential memory access violations or unauthorized data leakage between processes.



* MAC-Address Spoofing: To mitigate long-term tracking and network correlation risks, I have implemented an automated routine that dynamically rotates my device’s MAC address identifier on a daily schedule. This technique disrupts traffic continuity 
within logging infrastructures, thereby preventing entities from aggregating multi-day data streams to construct detailed behavioral profiles based exclusively on persistent hardware fingerprints.


* Mulvad VPN: VPNs shift trust from the ISP to the VPN provider. Thus when on untrusted networks, such as airport or hotel networks, using a VPN will prevent them from snooping on your traffic without significant effort. Additionally Mulvad is the only VPN provider beyond potentially ProtonVPN that has been proven not to keep logs.

[Top](#private-pad)

## Planned Features
* [I2p Connectivity](https://i2p.net/en/): The internet to peer projects is one of the best out there for web traffic privacy. The traffic is proxied between several users in a similar, but more distributed manner, to tor. Additionally the encrypted traffic is bundled with other users (this is called a clove, like cloves of garlic) in order to obfuscate who is doing what and help prevent fingerprinting. The end goal would to be to potentially enable communication between my devices over i2p, possibly as fully fleshed out messaging service but this is all in the pre-planning phase as of now.

* 3rd Party BIOS: Installing a 3rd party bios is one other way to disable the intel management engine on a more permanent basis. This would also allow total control over my firmware and would give me experience flashing the bios externally. 

[Top](#private-pad)
