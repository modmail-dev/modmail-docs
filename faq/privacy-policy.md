---
description: Sample Bot Privacy Policy that can be used by instances at their discretion
---

# Privacy Policy

> [!NOTE]
> This Privacy Policy only applies to Modmail Instances hosted by administrators who choose to use it. If a bot administrator has provided you this privacy policy, they have agreed to use it for their specific instance. If you have any questions regarding the validity of this privacy policy for any specific Modmail instance, please contact the relevant staff team.

Last Updated: June 17th, 2026

This Privacy Policy explains how Modmail (referred to as "the Bot", "we", or "us") collects, uses, stores, and protects your data. The Bot is an instance of the open-source [modmail-dev/modmail](https://github.com/modmail-dev/modmail) project and is hosted independently by the administrators of the Discord server.

By interacting with the Bot, you consent to the data practices described in this policy. This policy is designed to comply with the [Discord Developer Terms of Service](https://support-dev.discord.com/hc/en-us/articles/8562894815383-Discord-Developer-Terms-of-Service) and [Developer Policy](https://support-dev.discord.com/hc/en-us/articles/8563934450327-Discord-Developer-Policy).

## 1. Data We Collect

When you send a direct message to the Bot to initiate a support thread or interact with an active thread, we collect and store the following information:

1. **User Data:** Your Discord User ID, username, and avatar.
2. **Message Content:** The text content, attachments, and timestamps of any messages sent to the Bot.
3. **Server Data:** Relevant Guild (Server) IDs and Channel IDs required to route your messages to the correct moderation team.
4. **Action Logs:** Metadata related to the thread, such as when it was opened, closed, or transferred by moderators.

## 2. How We Store Your Data

The [modmail-dev/modmail](https://github.com/modmail-dev/modmail) application does not store data on Discord's infrastructure once a thread is archived ("closed"). Instead, all collected data (including message logs and user identifiers) is exported and stored off-platform in a MongoDB database.

This database is managed independently by the individual or team hosting the Bot instance. We implement reasonable security measures to protect your data from unauthorized access.

## 3. How We Use Your Data

The data we collect is strictly used to provide and maintain the functionality of the Bot. Specifically, we use it for:

1. **Facilitating Communication:** Relaying messages between you and the server's moderation or support staff.
2. **Record Keeping:** Maintaining an accurate history of support requests, appeals, or reports for server staff to reference.
3. **Service Improvement:** Allowing server administrators to review past interactions to improve community guidelines and support responses.

## 4. Data Sharing and Disclosure

Your data is highly restricted. We do not sell, monetize, or trade your personal information. Your data is only accessible to:

1. **Authorized Server Staff:** Moderators and administrators of the Discord server who have the necessary permissions to view Modmail threads and logs.
2. **The Database Administrator:** The technical individual responsible for hosting the MongoDB instance and keeping the Bot online.[^1]
3. **MongoDB Atlas Employees:** Select employees of the MongoDB Atlas team may have the ability to access the data. Their usage is restricted and governed by their [privacy policy](https://www.mongodb.com/legal/privacy/privacy-policy).

We will not share your data with any third parties unless explicitly required to do so by law or to comply with Discord's Trust and Safety requests.

## 5. Data Retention

Chat logs and associated user identifiers are retained indefinitely within our MongoDB database to ensure server staff have a consistent historical record of all moderation and support interactions.

## 6. Your Rights and Data Deletion

Under the Discord Developer Policies, you have the right to request the deletion of your personal data. If you wish to have your Modmail logs and associated identifying information permanently removed from our off-platform MongoDB database, you may exercise this right by:

1. Sending a message directly to the Bot requesting data deletion.
2. Contacting the server administrators or the contact person listed below.

Upon receiving a valid request, we will purge your identifying information and message content from our database within 14 days.

## 7. Contact Information

If you have any questions, concerns, or data deletion requests regarding this Privacy Policy or the Bot's operation, please contact:

1. The Bot directly; or
2. Any member of the server's staff team; or
3. The owner of the Discord server.

[^1]: In almost all cases, this is a member of the authorized server staff.

---

> [!NOTE]
> **Server Owners** — If you do not want this one size fits all option, you can use the template below as a starting point.

<details>
<summary>Basic Template</summary>

This Privacy Policy explains how `[Insert Bot Name]` (referred to as "the Bot", "we", or "us") collects, uses, stores, and protects your data. This Bot is an instance of the open-source [modmail-dev/modmail](https://github.com/modmail-dev/modmail) project and is hosted independently by the administrators of `[Insert Discord Server Name]`.

By interacting with the Bot, you consent to the data practices described in this policy. This policy is designed to comply with the [Discord Developer Terms of Service](https://support-dev.discord.com/hc/en-us/articles/8562894815383-Discord-Developer-Terms-of-Service) and [Developer Policy](https://support-dev.discord.com/hc/en-us/articles/8563934450327-Discord-Developer-Policy).

1. Data We Collect

When you send a direct message to the Bot to initiate a support thread or interact with an active thread, we collect and store the following information:

1. User Data: Your Discord User ID, username, and avatar.
2. Message Content: The text content, attachments, and timestamps of any messages sent to the Bot.
3. Server Data: Relevant Guild (Server) IDs and Channel IDs required to route your messages to the correct moderation team.
4. Action Logs: Metadata related to the thread, such as when it was opened, closed, or transferred by moderators.

2. How We Store Your Data

The [modmail-dev/modmail](https://github.com/modmail-dev/modmail) application does not store data on Discord's infrastructure once a thread is archived. Instead, all collected data (including message logs and user identifiers) is exported and stored off-platform in a MongoDB database.

This database is managed independently by the individual or team hosting this Bot instance. We implement reasonable security measures within the database environment to protect your logs from unauthorized access.

3. How We Use Your Data

The data we collect is strictly used to provide and maintain the functionality of the Bot. Specifically, we use it for:
1. Facilitating Communication: Relaying messages between you and the server's moderation or support staff.
2. Record Keeping: Maintaining an accurate history of support requests, appeals, or reports for the server staff to reference in the future.
3. Service Improvement: Allowing server administrators to review past interactions to improve community guidelines and support responses.

4. Data Sharing and Disclosure

Your data is highly restricted. We do not sell, monetize, or trade your personal information. Your data is only accessible to:

1. Authorized Server Staff: Moderators and administrators of `[Insert Discord Server Name]` who have the necessary permissions to view Modmail threads and logs.
2. The Database Administrator: The technical individual(s) responsible for hosting the MongoDB instance and keeping the Bot online.
    a. Database Administrator(s): `[Insert Names of Database Administrators Here]`
3. MongoDB Atlas Employees: Select employees of the MongoDB Atlas team may have the ability to access the data. Their usage is restricted and governed by their [privacy policy](https://www.mongodb.com/legal/privacy/privacy-policy).
4. `[Insert Name of Hosting Company]` Employees: Select employees of `[Insert Name of Hosting Company]` are able to access the data due to their ability to access the MongoDB connection information. Their privacy policy is defined [here](`[Insert URL to Hosting Company Privacy Policy Here]`).

We will not share your data with any third parties unless explicitly required to do so by law or to comply with Discord's Trust and Safety requests.

5. Data Retention

Chat logs and associated user identifiers are retained `indefinitely/(OR)[Insert Log Retention Time Here]` within our MongoDB database to ensure server staff have a consistent historical record of all moderation and support interactions.

6. Your Rights and Data Deletion

Under the Discord Developer Policies, you have the right to request the deletion of your personal data. If you wish to have your Modmail logs and associated identifying information permanently removed from our off-platform MongoDB database, you may exercise this right by:
1. Sending a message directly to the Bot requesting data deletion.
2. Contacting the server administrators or the contact person(s) listed below.

Upon receiving a verifiable request, we will manually purge your identifying information and message content from our database within [Insert Number, e.g., 30] days.

7. Contact Information

If you have any questions, concerns, or data deletion requests regarding this Privacy Policy or the Bot's operation, please contact us at:

1. Discord User(s): `[Insert Discord Username(s) of the Bot Owner/Administrator(s)]`
2. Email: `[Insert Contact Email, if applicable]`
3. Server: `[Insert Invite Link or instructions on how to reach staff]`

</details>

> [!IMPORTANT]
> **Server Owners**
>
> Please note that by using the Privacy Policy on our Docs site without modification, you are making legally binding promises to your users and to Discord. These promises include, but are not limited to:
>
> **1. Strict Data Sharing Limitations**
>
> You are agreeing that you will not share user data with any third parties unless required by law. This means you cannot share Modmail logs with other Discord servers, community ban lists, global moderation databases, or any external entities. If you do so: you are violating this privacy policy, which could carry civil penalties in some jurisdictions.
>
> **2. Infrastructure and Hosting Trust**
>
> The policy states that only server staff and the database administrator have access to the logs. You must ensure that your hosting provider and your database host are secure and trustworthy. If your hosting provider has weak security and your database leaks, the responsibility falls entirely on you. *(This is primarily a concern for individuals using hosting providers that are not established, see our comments on [unrecommended hosts](../choose-host/unrecommended-hosts.md).)*
>
> **3. Binding Deletion Timelines**
>
> If you state that you will delete data upon request within 14 days, you must have a reliable, manual process to find and purge a user's data from your MongoDB cluster within that exact timeframe. Failure to honor data deletion requests is a direct violation of the Discord Developer Terms of Service and can result in action taken against your account. If you fail to honor this you also: are violating this privacy policy, which could carry civil penalties in some jurisdictions.
>
> **4. Managing Staff Access**
>
> Because your policy guarantees that only authorized staff have access to user data, you must rigorously manage permissions. When a moderator steps down or is removed from your team, you must immediately revoke their access to the Modmail bot commands, the database, and the log viewer. If you fail to do so: you are violating this privacy policy, which could carry civil penalties in some jurisdictions.
>
> **5. Regional Privacy Laws**
>
> Depending on where you and your users reside, you may be subject to strict data protection laws like the GDPR in Europe or the CCPA in California. These laws impose significant obligations regarding data handling, consent, and user rights, even for hobbyist or volunteer-run Discord servers.