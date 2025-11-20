---
description: This page briefly describes our recommendations for choosing a host.
---

# Choosing a Host

Choosing where to host your Modmail bot is one of the most important decisions you’ll make during setup. A good host can make your Modmail bot invaluable for running your server, a bad host can make it useless.

There are three main factors to balance when selecting a host:

1. **Cost**  
2. **Availability (Uptime)**  
3. **Simplicity**

{% hint style="info" %}
If you’re looking for specific providers that have been tested by our community, check the [Recommended Hosts](recommended-hosts.md) page.  
You can also view hosts that are **not suitable** for Modmail on the [Unrecommended Hosts](unrecommended-hosts.md) page.
{% endhint %}

---

## Understanding the Tradeoffs

No hosting option is perfect — choosing where to host your bot always means balancing cost, uptime, and simplicity.

You may have heard the saying *“cheap, good, fast — pick two.”* Hosting Modmail (or any Discord bot) follows a similar idea. In our case, the three factors are **Cost**, **Uptime**, and **Simplicity**. You can usually get two of them, but you’ll have to compromise on the third. Here’s a quick overview:

| Low Cost | High Uptime | Simple | Example                |
| -------- | ----------- | ------ | ---------------------- |
| ✅        | ❌           | ✅      | Free Pterodactyl Panel |
| ✅        | ✅           | ❌      | Private VPS            |
| ❌        | ✅           | ✅      | Heroku                 |


{% hint style="warning" %}
**Free Hosting Platforms are Discouraged**

Over the years, the Modmail team has spent many hours researching and recommending free hosting platforms. Starting in 2025, we are no longer spending the time, or recommending platforms purley for being free.

Free platforms usually have, or develop one of these problems: remove free tier, high downtime, problematic server connection, terminating instances without notice.


{% endhint %}

### "Minimum Spec"

The Modmail project does not have a minimum specification required to use run your bot. However, generally, if you hear anyone from our team, or read on this page the term "minimum spec" or "min spec", we are referring to this:

|System Spec|Minimum Value|
|-|-|
|CPU|1 core, speed mostly irrelevant|
|RAM|1GB|
|Storage|~2GB (on top of OS)|
|Network Speed| > 10 Mbps|
---

## Hosting Decision Flow

{% stepper %}
{% step %}
### Step 1 — Identify Your Needs
Modmail is a very lightweight bot, very minimal resources are required.

> Do you have more than 1000 members in your server?

If not: you likely do not need more than 512mb of memory and 1 CPU core.

If yes: you can potentially get away with the minimum spec, but you should consider upgrading.

> Do you require your Modmail bot to be online with 0 downtime?

If yes: you want to steer away from free hosts, and in most cases, local hosting as well.

> Do you plan to have significant usage of your bot?

If yes (ie plugins, hundreds of active threads at once - being replied to not sitting dormant, etc): you can potineitally get away with the minimum spec, but you should consider upgrading.

If you aren't sure: Talk with our [community and team](https://discord.gg/nfErcs7mDM).

If no: use the minimum spec above.

> How technical are you?

If you struggle with technology, you may want to consider a PaaS (Platform as a Service) host, which handles the backend of a server for you. If you have strong technical proficiencies, a VPS or local hosting is likely a better fit for you.

{% endstep %}

{% step %}
### Step 2 — Decide on Your Budget
- **$0:** Not recommended. Free hosts are unstable and may terminate at any time.  
- **$2–10/month:** Ideal for most users. Reliable cloud or VPS hosting with full control.  
- **$15+/month:** Used for hosting multiple **large** modmail bots and/or extra services besides modmail. Unnecessary for hosting a single modmail bot.
{% endstep %}

{% step %}
### Step 3 — Pick Your Platform Type
| Platform Type | Best For | Pros | Cons | Examples | 
|-----------|-----------|------|------|-|
| **PaaS** | Simple setup requiring less technical knowledge | Simple UI, auto-deploys, managed | Paid Plan usually Required | Heroku, Railway| 
| **Hetzner / OVH / DigitalOcean (VPS)** | Users with basic technical knowledge | Full control, high uptime | Linux/Docker setup required | See [Recommended Hosts](../choose-host/recommended-hosts.md) |
| **Local Hosting** | Users with special cost requirements, or other locally running, always on, computer at home. | No subscription, complete control | Local outages affect uptime | Old Computer, Raspberry Pi, etc|
{% endstep %}
{% endstepper %}


## Related Pages
- [Recommended Hosts](../choose-host/recommended-hosts.md) — Tested VPS and PaaS providers our users trust.
- [Unrecommended Hosts](../choose-host/unrecommended-hosts.md) — Platforms known to cause Modmail reliability issues.


{% hint style="success" %}
### Our Recommendation for Most Users
For nearly all cases, we recommend a cheap Virtual Private Server from one of our [Recommended Hosts](../choose-host/recommended-hosts.md).

For users who do not wish to pay, we recommend locally hosting the bot from hardware you already own, like a Raspberry Pi, or old computer you can keep running 24/7 in your house.

In situations where you significantly struggle with technology, a PaaS option *may* be better with you. Feel free to consult with our [team](https://discord.gg/nfErcs7mDM) if you don't know if this is the best option for you.
{% endhint %}

{% hint style="danger" %}
### A Caution on Free Pterodactyl based hosts.

Many hosting "companies" have popped up in recent years using the free, open source, [Pterodactyl](https://pterodactyl.io/) hosting platform. These hosting sites are particularly problematic. With the biggest concern usually revolving around **your data security**. Many, if not all, of these platforms do not provide, possess, or follow proper agreements relating to the access of your uploaded information. This includes your MongoDB Conncection URI, and Bot Token, allowing the "staff" of these "companies" to access any message ever sent to or from your bot, any message in your server, and carry out actions as your bot (ie. deleting channels, reading messages, banning users).

Additionally, many of these hosts are run with substandard hardware and infrastucture, usually resulting to temporary IP bans from Discord, poor uptime, poor performance, improper dependancy installation, and more.

We **strongly** encourage you to conduct **full and complete** research before using these hosts. *Our general recommendation is to: avoid them.*

{% endhint %}