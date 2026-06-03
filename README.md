EaglerCraft Server Utilities

Welcome to the EaglerCraft Server Utilities repository!

This project provides a growing collection of Skript scripts, configuration examples, and small utility snippets designed specifically for EaglerCraft / 1.8–1.12 style servers.


If you run an EaglerCraft server and want fun, troll‑style commands, simple economy features, and basic security/auth systems without writing full Java plugins, this repo is for you.




Note: This project focuses on Skript‑based solutions and simple configs. It is not a full plugin framework. Everything here is meant to be easy to drop into your existing EaglerCraft server setup.




Table of Contents


Overview

Features

Included Scripts

Hack Command (hack.sk)

Emergency Kick / Shutdown (eshut.sk)

Economy & Permissions Example (permissions.yml)



Installation

Requirements

Setting Up Skript

Adding the Scripts



Configuration

Permissions

Customizing Messages

Adjusting Timers and Costs



Usage Examples

Admin Workflow

Typical Player Experience



Roadmap

Contributing

Support & Feedback

License



Overview

Running a Minecraft‑style EaglerCraft server on the web is fun—but it also comes with unique challenges:



Many hosting environments are limited (no full access to plugins or Java dev tools).

Server owners often want simple, fun features quickly (troll commands, basic economy, player shops) without learning Java or building complex plugins.

EaglerCraft players love servers that feel customized and interactive, even when the backend is lightweight.


This repository exists to bridge that gap. It provides ready‑to‑use Skript scripts and configuration examples you can drop into your server to add:



Simple admin commands

Fun troll utilities

Lightweight economy and permissions examples

Basic quality‑of‑life improvements


All of this is built with the goal of being:



Easy to understand – scripts are written as simply as possible.

Easy to customize – messages, permissions, and behavior are clearly labeled.

Safe to experiment with – no world‑destroying behavior unless you intentionally add it.


If you are new to Skript or just want pre‑made utilities for an EaglerCraft environment, this repo gives you a starting kit you can expand over time.



Features

High‑level features you’ll find (or that are planned) in this repository:




Admin‑only “hack” command

Fake “/hack” command for trolling admins or staff. Triggers a kick with a custom message.




Emergency shutdown / mass‑kick command

/eshut lets admins kick all players after a delay, simulating a shutdown or maintenance event.




Simple economy variable usage

Examples showing how to use {money.%player%} as a basic currency store, including starting balances and admin commands like /setbal.




Permissions structure examples

A permissions.yml that demonstrates how to gate different commands behind simple permissions, so only admins can trigger powerful actions.




EaglerCraft‑friendly design

Scripts are designed with Eagler hosts and web‑style panels in mind—minimal dependencies, straightforward reload commands, and compatibility with typical 1.8–1.12 environments.




As the repository grows, more utilities will be added: mini‑auth systems, player shops, UI helpers, join fees, and more.



Included Scripts

Hack Command (hack.sk)

The hack.sk script adds a troll command that lets admins “hack” themselves or other players. When used, it kicks the target with a custom message such as:




"You've been hacked"



Key behaviors:



Only players with the right permission (or ops) can use /hack.

The script can be configured to:

Kick the sender only (self‑hack).

Optionally accept a target player argument to kick other players.



The script uses simple syntax to stay compatible with older Skript builds.


This is ideal for EaglerCraft servers where you want lighthearted trolling commands without actually damaging the world or players’ data.



Emergency Kick / Shutdown (eshut.sk)

The eshut.sk script provides an emergency mass‑kick command. Although the original concept was a full shutdown, the safer and more Eagler‑friendly behavior is:



/eshut <seconds> – broadcasts a warning and then kicks all players after the specified number of seconds.


For example:


/eshut 30

This will:



Broadcast a clear message that everyone will be kicked in 30 seconds.

Wait for 30 seconds, giving players time to finish what they’re doing.

Kick all players with a friendly maintenance message.

Leave the server running so players can reconnect once you’re ready.


Why this is useful:



Quickly clear the server before maintenance, restarts, or config changes.

Avoid surprise disconnects by always giving a countdown.

Admin‑only access via eshut.use permission keeps it safe.



Economy & Permissions Example (permissions.yml)

The repository also includes an example permissions.yml that demonstrates how to:



Define permissions like:

hackcommand.use – allows /hack

eshut.use – allows /eshut

Custom economy/admin perm nodes (e.g., for /setbal, /lockinv, etc.)



Set default: op where you want only ops to have the permission.

Provide descriptive text for each node so you remember why it exists.


This example file is not mandatory, but it gives you a working template you can adapt to your own server.



Installation

Requirements

To use the scripts in this repo, you should have:



An EaglerCraft‑style server based on Spigot/Paper 1.8–1.12 or similar.

The Skript plugin installed (a version compatible with your server).

Access to your server’s plugins/Skript/scripts/ folder via your hosting panel or FTP.


If you’re running on a typical Eagler host, your control panel should already have:



A plugins folder

A Skript folder inside it

A scripts directory where .sk files go


If you don’t see these, you may need to:



Upload the Skript plugin JAR to plugins/, then restart your server.

Or enable Skript from your hosting provider’s plugin list.


Setting Up Skript


Download a compatible version of Skript for your Minecraft / Eagler version (for example, Skript 2.6 for 1.12.2).

Place the Skript JAR in your server’s plugins folder.

Start (or restart) the server.

Confirm that a plugins/Skript folder was created.


Adding the Scripts



Navigate to plugins/Skript/scripts/ in your file manager.




Upload the .sk files from this repo (e.g. hack.sk, eshut.sk) into that folder.




In the server console, run:


/skript reload all

or reload individual scripts, for example:


/skript reload hack
/skript reload eshut



Watch the console for any error messages. If there are errors, double‑check:



Your Minecraft / Eagler version

Your Skript version

Whether the script was pasted correctly without extra or missing lines




Once the reload completes without errors, the commands from these scripts will be available in‑game.



Configuration

Permissions

The repo assumes a simple permissions model. Here are some of the key permission nodes you might use:



hackcommand.use – allows using /hack

eshut.use – allows using /eshut

playershop.setbal – allows /setbal <player> <amount> style commands

joinfee.free – exempts admins from join fees in advanced examples

lockscreen.use – allows /locks and /unlocks in lock‑screen scripts (if you add them)


In a basic permissions.yml, a node might look like:


permissions:
  hackcommand.use:
    description: Allows use of /hack
    default: op
  eshut.use:
    description: Allows use of /eshut shutdown command
    default: op

If you use a more advanced permissions plugin (like LuckPerms), you can set these with in‑game or console commands instead.


Customizing Messages

Every script is designed to use clear, editable messages. Look for send or kick lines in the .sk files, for example:


kick player due to "You've been hacked"

You can change these to match your server’s theme or language, for example:


kick player due to "&cHacked! &7You have been disconnected by the system."

Color codes like &a, &c, and &7 are supported in most Minecraft contexts; Skript will pass them on to the server as usual.


Adjusting Timers and Costs

Some scripts use wait or numeric values to control behavior. Examples:




eshut.sk – the delay before kicking:


wait {_t} seconds



Join fee scripts – how many coins you start with and how much each join costs.




You can safely change these numeric values to match your server’s economy speed and gameplay style. Just keep them as whole numbers and keep an eye on your console after reloading to ensure there are no syntax issues.



Usage Examples

Admin Workflow

Here are some typical actions an admin might take with these scripts installed:




Trolling an admin friend with /hack:



Make sure they have hackcommand.use (or are op).

They type /hack on themselves or you run a version that targets them.

They get kicked with a fake “You’ve been hacked” message.




Running a scheduled maintenance kick with /eshut:



Before making changes, run:
/eshut 60


All players see a warning that everyone will be kicked in 60 seconds.

After 60 seconds, everyone is kicked with a maintenance message.

You make your changes and let players know they can reconnect.




Managing player balances with /setbal:



If you add a /setbal command in your economy script, you can do:
/setbal PlayerName 1000


This is useful for events, rewards, or resetting a broken balance.




Safely testing new scripts:



Upload a new .sk file.

Use /skript reload <name> instead of reloading everything.

Test the command with a non‑op account to confirm permissions behave correctly.




Typical Player Experience

From a regular player’s point of view, the utilities in this repo can:



Create fun and unpredictable moments (like the hack command being used on admins or staff).

Provide basic economy feedback (balance, shop interactions, future join‑fee or shop scripts).

Help keep the server stable by making admin tools more accessible and predictable.


Because these scripts are lightweight and focus on simple interactions, they’re unlikely to cause lag or confusion when configured correctly.



Roadmap

This repository is meant to grow over time. Planned or possible additions include:



Player shop systems using chests and signs, so players can sell items to each other.

Lock/unlock utilities to freeze players in place (for moderation or events).

Join fee/ticket systems where each login consumes a small amount of in‑game currency.

Basic auth/login helpers (for servers that want a minimal registration step without a full auth plugin).

UI helpers using chat, titles, or sidebars (where supported) to show balance, server info, and announcements.


All of these will be built with the same goals: clarity, simplicity, and compatibility with EaglerCraft‑style setups.


If there is a particular feature you’d like to see here, feel free to open an issue or start a discussion in the repository.



Contributing

Contributions are very welcome, especially if you:



Run an EaglerCraft server and have battle‑tested scripts you want to share.

Have ideas to simplify or improve the existing scripts.

Want to add documentation, comments, or examples to help new server owners.


How to Contribute



Fork this repository on GitHub.




Create a new branch for your changes:


git checkout -b feature/my-cool-utility



Add your .sk files or modify existing ones.




Test them on a local or staging EaglerCraft server if possible.




Commit with a clear message and push your branch.




Open a Pull Request explaining:



What the script does.

Which versions of Minecraft / Skript you tested on.

Any permissions or config needed.




Please keep scripts:



As clear and commented as possible.

Safe by default (no accidental world destruction).

Focused on EaglerCraft‑friendly use cases.



Support & Feedback

If you have questions, run into errors, or want to request a new utility, you can:



Open an Issue on this GitHub repository with:

Your server/Minecraft version

Your Skript version

The script name and error message (if any)



Use GitHub Discussions or comments if you enabled them to ask for help or suggest ideas.


When reporting problems, please include:



The exact error lines from your server console (copy/paste).

A short description of what you expected vs. what actually happened.

Any modifications you made to the original script.


This makes it much easier to debug and improve the utilities in this repo.



License

You are free to:



Use these Skript files on your own EaglerCraft or Minecraft server.

Modify them to fit your needs.

Share your modified versions, as long as you give appropriate credit and clearly mark your changes.


If you re‑publish these scripts or include them in a public pack, a simple note such as:




"Based on scripts from the EaglerCraft Server Utilities repository (dkjdjjfkd/eagler)."



is appreciated.



Final Notes

This repository is a living collection of simple, practical tools for EaglerCraft server owners. It’s not meant to be perfect or complete—but it should give you a strong starting point and save you hours of trial and error.


Check back periodically for new scripts and improvements. If you enjoy using these utilities, consider starring the repo on GitHub and sharing it with other EaglerCraft server owners.


Happy hosting! :)
