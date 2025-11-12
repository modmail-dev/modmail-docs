# Thread Menu

{% hint style="info" %}
This page will provide information on using the `?threadmenu` core bot functionality. If you are still using the `advanced-menu` plugin from Sebkuip, please migrate away from the plugin before attempting to use these features.

Migration Instructions are at the bottom of this page.
{% endhint %}

The Thread Menu `?threadmenu` function allows recipients to choose an option to better clarify what kind of help they are recieving. It supports submenus, command, and text-based replys allowing a complex and efficient thread routing system.

## Config Options

|  Config Variable Name  | Type |  Default  | Details | 
| - | - | - | - |
| thread_creation_menu_anonymous_menu | Boolean (`yes/no`)  | No | If enabled, the initial menu prompt relayed to staff (after creation) is anonymized; only selection details are logged, not the original prompt message author context. |
| thread_creation_menu_close_on_timeout | Boolean (`yes/no`) | No | Silently aborts thread creation if the user does not select an option before the timeout expires. |
| thread_creation_menu_dropdown_placeholder | Text | "Select an option to contact the staff team."  | Placeholder text displayed in the dropdown before selection. |
| thread_creation_menu_embed_color | Hex Code (or Discord Color) | Green | Color for the menu embed's side strip. Accepts hex (e.g. #5865F2) or one of the supported color names (e.g. "blurple"). |
| thread_creation_menu_embed_footer | Text | Empty (no footer) | Optional footer text at the bottom of the menu embed. |
| thread_creation_menu_embed_footer_icon_url | URL | Empty (no icon) | Optional URL for the small footer icon displayed next to the footer text. |
| thread_creation_menu_embed_image_url | URL | Empty (no image)  | Optional large hero image displayed in the body of the menu embed. If set, this image is shown prominently and takes precedence over the thumbnail. |
| thread_creation_menu_embed_large_image | Boolean (`yes/no`) | No | Promotes the thumbnail to a large hero image when no `thread_creation_menu_embed_image_url` is set. Useful if you want a big image without specifying a separate URL. |
| thread_creation_menu_embed_text | Text | "Please select an option." | Text shown in the embed above the selection dropdown in the user's DM. |
| thread_creation_menu_embed_thumbnail_url | URL | Empty (no thumbnail) | Optional thumbnail image shown in the top-right of the menu embed. |
| thread_creation_menu_embed_title | Text | Empty (no title) | Optional title at the top of the thread-creation menu embed in the user's DM. |
| thread_creation_menu_precreate_channel | Boolean (`yes/no`) | No | When enabled, a thread channel is created immediately upon the user's first DM even if the thread creation menu is enabled. The menu is still shown but selection becomes optional and happens after channel creation. |
| thread_creation_menu_selection_log | Boolean (`yes/no`) | Yes | When disabled, the staff will not see an automatic message with the selection details though commands may still act. |
| thread_creation_menu_timeout | Time in Seconds | 30 | If the timeout is reached, `thread_creation_menu_close_on_timeout` controls whether the attempt is aborted or the user is asked to message again.|


## Commands

- threadmenu
├─ dump_config - Dump the current core thread menu config to a file.
├─ load_config - Load the thread menu config from an attached file.
├─ option - Manage main-menu options (add/remove/edit/show).
    ├─ add - Interactive wizard to add a main-menu option.
    ├─ edit - Interactive wizard to edit a main-menu option.
    ├─ remove - Remove a main-menu option by label.
    └─ show - Show detailed information about a main-menu option.
├─ reset - Reset ALL thread-creation menu settings to their defaults.
├─ show - Show all current main-menu options.
├─ submenu - Manage submenus (create/delete/list/show and options within).
    ├─ create - Create an empty submenu that can hold nested options.
    ├─ delete - Delete a submenu and all its options.
    ├─ list - List all submenu keys currently configured.
    ├─ option - Manage options within a specific submenu (add/remove/edit).
        ├─ add - Interactive wizard to add an option inside a submenu.
        ├─ edit - Interactive wizard to edit a submenu option.
        └─ remove - Remove an option from a submenu via an interactive prompt.
    └─ show - Show the options configured inside a submenu.
└─ toggle - Enable or disable the thread-creation menu.

## Example Flowchart and Command Order

{% hint style="info" %}
This feature allows the creation of very complex menu systems. If you are intending to create a complex menu system, it is recommended to think through the required submenus and options and make your submenus first. Drawing these out in a flowchart like below is a good way to begin this process.
{% endhint %}

{% tabs %}

{% tab title="Flowchart Example" %} **In Progress by theonlystephen** {% endtab %}

{% tab title="Commands Example" %} **In Progress by theonlystephen** {% endtab %}

{% tab title="Flowchart Template" %} **In Progress by theonlystephen** {% endtab %}

{% endtabs %}

## Advanced/Legacy Usage

<details>

<summary>Migrating from Legacy `advanced-menu` Plugin</summary>

Migration from the legacy plugin, to core function requires permission to modify the menu. In both, by default, this level is ADMINISTRATOR [4].

**Step 1: Export Config from `advanced-menu`**

Run the `?advancedmenu dump_config` command to dump the menu config from `advanced-menu`. This will export your menu configuration to a `config.json` file.

[image]

**Step 2: Download `config.json` to your local computer**

Press the download button and keep track of where the file was saved. You will need it in the next step.

**Step 3: Import Config to Thread Menu**

Run the `?threadmenu load_config` command, while attaching the downloaded `config.json` to your message.

**You're done!**

Good job! You have successfully migrated your `advanced-menu` config to the Thread Menu feature introduced in Modmail 4.2.0.

</details>
<details>

<summary>Menu `.json` File Structure</summary>

{% hint style="warning" %}
This is an **advanced** concept, and is **not** required to make full use of this feature. If you do not have significant experience working with `.json` files, you should not be using any of the information in this section.
{% endhint %}

The `?threadmenu dump_config` command exports your set menu configuration to a `.json` file.

By default, the file is now called `thread_creation_menu_config.json`. You can rename this file without any issue while reimporting.

Note: the `"category_id":` in each menu option is optional, and not required for successful import.

See an example dumped config below:
```json
{
  "enabled": true,
  "options": {
    "discord_events_issues": {
      "label": "Discord Events Issues",
      "description": "I have questions about Discord Events",
      "emoji": "⚠️",
      "type": "command",
      "callback": "move 1341094680229843026 && anonreply Please provide additional details about the event and the issues you encountered so we can help you out."
    },
    "report_member(s)": {
      "label": "Report Member(s)",
      "description": "I want to report a Discord member",
      "emoji": "🚨",
      "type": "command",
      "callback": "move 1341094680229843031 && anonreply Please share any relevant information regarding the member(s) involved, along with a description of the incident.",
      "category_id": 1341094680229843031
    },
    "discord_related_issues": {
      "label": "Discord Related issues",
      "description": "I have questions regarding the server",
      "emoji": "🛠️",
      "type": "command",
      "callback": "move 1341094680770642004 && anonreply Please describe the issue you're facing in detail so that we can help resolve it as quickly as possible.",
      "category_id": 1341094680770642004
    },
    "discord_appeal": {
      "label": "Discord Appeal",
      "description": "I want to appeal a Discord ban",
      "emoji": "🎟️",
      "type": "command",
      "callback": "move 1341094680770642007 && anonreply Please provide any additional context or evidence that supports your appeal, and we'll review it promptly.",
      "category_id": 1341094680770642007
    },
    "others": {
      "label": "Others",
      "description": "My question was not listed",
      "emoji": "❓",
      "type": "command",
      "callback": "move 1341094680770642004 && reply Please let us know the details of your request so we can assist you appropriately.",
      "category_id": 1341094680770642004
    }
  },
  "submenus": {},
  "timeout": 45,
  "close_on_timeout": true,
  "anonymous_menu": false,
  "embed_text": "Please select an option.",
  "dropdown_placeholder": "Select an option to contact the staff team."
}
```

</details>
