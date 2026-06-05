---
description: These hosts are hosts we, and members of our community have had little success with.
---

# Unrecommended Hosts

{% hint style="warning" %} The Modmail team does not in any way intend to defame, harm, or otherwise create badwill between Modmail and the open source community as a whole, and any hosting provider. We simply provide this list to our users through our experience. We do not in any way imply that these hosts are bad, unreliable, or that it is not possible to use them, we simply state that these are not a good fit for hosting Modmail. {% endhint %}

### Repl.it

- [Website](https://repl.it)
- Repl.it is a provider aimed at hosting websites. Meaning, it does not have the proper tools and features to properly host the Modmail bot.
- This host is particularly problematic, and there have been many documented unexplainable issues that occur when hosting your bot with this method. Because of this it is **strongly discouraged** for use.

### Bot-hosting.net

- [Website](https://bot-hosting.net/)
- bot-hosting.net is a free or low cost hosting provider that bases their hosting platform on the common free and open-source panel [Pterodactyl](https://pterodactyl.io/).
- Hosting on any Pterodactyl panel based host is already challenging, however, bot-hosting.net shares IP addressess among users, which has resulted in high numbers of our users reporting rate limits being applied to their bot. In other words: your bot will randomly stop working with nothing you can do to fix it.

### Wispbyte

- [Website](https://wispbyte.com/)
- Similar setup and issues as Bot-Hosting.net — shared resources and inconsistent reliability.  
- Wispbyte's support team has also been seen to suggest random breaking changes to attempt to make the bot run. They do not work.

### Karlo Hosting
- [Website](https://karlo-hosting.com/)
- Another free or low cost hosting provider based on the Pterodactyl panel, our users have reported unusual difficulties deploying Modmail with this host due to their specific Pterodactyl configuration and limitations.

### Discord Bot Hosting
- [Website](https://discordbothosting.com/)
- Pterodactyl based host that can have issues with ratelimits due to shared IP addresses and reasons that have been listed above.

### Kairo Hositing
- Discord Only
- Kairo Hosting is a discord server based hosting provider that provides free hosting for Modmail bots. However, the Modmail team was provided evidence that the host expressed what is in our opinion, poor security hygiene, by failing to isolate the filesystems of bots. This allows any user hosting with Kairo hosting to access all files, including token and database connection details of all other bots hosted by this provider. This is a major security risk, with this, we have no choice but to not recommend this host.
<details>

<summary>1x Screenshot</summary>

![The eval command can be used to access the local system, including all files on the computer, and the files for other bots.](../.gitbook/assets/Discord_jqmKMh1cR9.png)

</details>

<details>

<summary>Stephen from the Modmail Team's Update on May 30th, 2026</summary>

> The Modmail team always attempts to work in good faith with a host when we find a security vulnerability. We have been working with this host and it appears they are making a good faith attempt to address the security vulnerabilities we have found. Even after these fixes, we still advise caution when using this host.

</details>

### baud.host
- [Website](https://baud.host)
- baud.host is a low cost hosting provider that is primarily operated by Kybo Group, a Roblox products group.
- baud.host does not allow users to provide their MongoDB Connection URI, this is not recommended as it locks users into a single host, and limits a user's ownership of their data. We were not able to conduct a test on the security of their locally hosted database, but if managed improperly, it could also be a security concern.
- baud.host uses Stripe for payment verification, however, appears to use their own processing flow, instead of the one provided by Stripe. We were unable to conduct a test on security, but this could be a security concern.
- Kybo Group claims compliance with HIPAA, GDPR, DPDPA, with an ISO27001, PCI DSS, SOC 1 Type 2, and SOC 2 Type 2 certifications, however, attempts to verify this have failed. You can conduct your own certification search with the [IAF](https://www.iafcertsearch.org/search/certified-entities?search=Kybo%20Group).
- Some users have reported features in latest updates not working with this host.


{% hint style="danger" %}
### Why These Are Not Recommended
These hosts generally:
- Use **shared or oversold Pterodactyl setups**  
- Offer **free or ultra-low-cost tiers** with limited resources  
- Experience **rate limits, sleep periods, or unresponsive containers**  
- Provide **no control over environment configuration**
- Hide **legal information regarding their business or company**

If you value stability, security, and consistent uptime, avoid free or oversold shared hosts.  
Refer to [Choosing a Host](../choose-host/README.md) for guidance on reliable alternatives.
{% endhint %}
