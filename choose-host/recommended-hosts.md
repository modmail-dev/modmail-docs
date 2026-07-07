---
description: These hosts are hosts we, and members of our community have had success with.
---

# Recommended Hosts

{% hint style="info" %} The Modmail Team does not have any affiliation with any hosting providers or platforms. {% endhint %}

## Official Modmail Hosting

The Modmail team provides official hosting of the bot using Buy Me a Coffee. Monthly plans start at $4/month.

Most plans also include premium logviewer, which allows locking a Loglink using OAuth Discord Login, and a dashboard.

Official Hosting is run on redundant servers with automatic failover.

See details on [Buy Me a Coffee](https://buymeacoffee.com/modmaildev/membership).

## VPS Providers

### ✦ Large Providers:
[Hetzner](<https://www.hetzner.com/cloud>) (DE†) ↦ Cloud - CAX11 for $4.10/mo. †US region also available for an extra 61¢ (CPX11).

[OVHCloud](<https://www.ovhcloud.com/en/vps>) (CA) ↦ VPS - Starter for $4.20/mo.

### ✦ Lesser-Known Providers:
[GalaxyGate](<https://galaxygate.net/hosting/vps>) (US) ↦ VPS - Standard 2GB for $5.00/mo.


[Netcup.eu](<https://www.netcup.eu/vserver/vps.php>) (DE) ↦ vServer - VPS 200 G10s for $3.52/mo. (6 mo. contract).


[HostHatch](<https://hosthatch.com/products>) (US) ↦ Compute VMs - NVMe 2 GB for $4.00/mo.

### ✦ Other Reliable Providers:
[BuyVM](<https://buyvm.net/kvm-dedicated-server-slices>) 

[Digital Ocean](<https://www.digitalocean.com/products/droplets>) 

[Linode](<https://www.linode.com/products/shared>) 

[Tier.net](<https://www.tier.net/vps>)

[Vultr](<https://www.vultr.com/products/cloud-compute>)

[IONOS](<https://www.ionos.ca/servers/vps>)

### ✦ Budget Providers: Cheap! But Less Reliable.

[HostVDS](<https://hostvds.com/#cloud>) (US) ↦ Cloud VDS - 1 vCPU 2 GB for $1.99/mo.

[RackNerd](<https://www.racknerd.com/NewYear/>) (US) ↦ Intel KVM VPS - 2 GB KVM VPS for $17.38/yr.


{% hint style="info" %} Pricing current as of time of publication, October 5th, 2024. Check websites for up to date pricing information {% endhint %}

{% hint style="warning" %} Be sure to research hosting providers before renting a server from one. Our recommendations and experiences should be used as recommendations only, we cannot guarantee any specific experience with any provider, nor can we provide billing or other support regarding the operating system, or availability of servers. Support is only provided through the process of installing and maintaining Modmail itself. {% endhint %}

{% hint style="info" %} The Modmail Team always recommends exercising security best practices with any server. While we are unable to provide official support on this matter, we can recommend some good places to start:

- [Digital Ocean](https://www.digitalocean.com/community/tutorials/an-introduction-to-securing-your-linux-vps)
- [Plesk Recommendations](https://www.plesk.com/blog/various/how-to-secure-your-linux-server-a-detailed-guide/#)
- [ninjaOne Recommendations](https://www.ninjaone.com/blog/key-steps-for-a-more-secure-linux-server/)
- [Linux.org Fourms Recommendations](https://www.linux.org/threads/the-ultimate-guide-to-reasonable-security-for-your-debian-ubuntu-linux-server-for-new-linux-admins.49199/)

    *Consider these a starting point, but be sure to do your own research. The Modmail Team holds no liability for any security mishaps that may occur with a server not rented by us and under our full, direct, and exclusive control. (in other words: we aren't responsible for your server)*

 {% endhint %}

## PaaS Providers

PaaS Hosting is usually more expensive, but a simpler to setup solution, which removes the need for securing a server, SSH configurations, terminal usage, and similar. However, because of this the platforms are usually more restricted, and difficult to troubleshoot. Despite this they are still an adequate and supported option.

[Heroku](https://www.heroku.com/)

[Railway](https://railway.com/)

{% hint style="danger" %}
## A Caution on Free Pterodactyl based hosts.

Many hosting "companies" have popped up in recent years using the free, open source, [Pterodactyl](https://pterodactyl.io/) hosting platform. These hosting sites are particularly problematic. With the biggest concern usually revolving around **your data security**. Many, if not all, of these platforms do not provide, possess, or follow proper agreements relating to the access of your uploaded information. This includes your MongoDB Conncection URI, and Bot Token, allowing the "staff" of these "companies" to access any message ever sent to or from your bot, any message in your server, and carry out actions as your bot (ie. deleting channels, reading messages, banning users).

Additionally, many of these hosts are run with substandard hardware and infrastucture, usually resulting to temporary IP bans from Discord, poor uptime, poor performance, improper dependancy installation, and more.

We **strongly** encourage you to conduct **full and complete** research before using these hosts. *Our general recommendation is to: **avoid them.***

{% endhint %}