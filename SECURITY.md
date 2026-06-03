Security Policy

Supported Versions

This project is developed and maintained on a best‑effort basis. Because it consists mainly of Skript files and simple configuration examples for EaglerCraft / Minecraft‑style servers, there is no formal version support matrix.


However, in general we focus on compatibility with:



Minecraft / EaglerCraft versions: 1.8 – 1.12.x

Skript versions: those commonly used with the above server versions (for example Skript 2.1+ / 2.2 / 2.6 on 1.12.2)


If a specific script, feature, or configuration only works on a narrow version range, it should be documented in that file. If you discover a compatibility or security issue, please report it as described below.


Reporting a Vulnerability

If you believe you have found a security vulnerability in this repository or in any script/configuration contained here, please follow these steps:




Do not disclose the issue publicly yet.

Avoid opening a public GitHub issue or posting the details on social media or community chats until it has been reviewed.




Contact the maintainer privately.

Use one of the following options:



Open a GitHub issue with minimal detail, marking it clearly as a potential security problem, and request a private channel for full details.

If a direct email address is listed on the maintainer’s GitHub profile, send a message there including:

A short description of the issue.

Steps to reproduce (if applicable).

Why you believe it is a security concern (data leak, privilege escalation, remote code execution, etc.).






Provide clear, reproducible information.

When reporting:



Include the exact script(s) or file(s) affected (file name and path).

Include the server version, Skript version, and any other relevant plugins.

If possible, include minimal sample configuration or commands that trigger the issue.

If screenshots or logs help, you may attach them after we agree on a safe sharing method.




Allow time for investigation and a fix.

Once a report is received, the maintainer will:



Confirm receipt of your report (usually within a few days).

Investigate the issue and attempt to reproduce it.

Decide on appropriate mitigation or fixes.

Prepare patched scripts and/or documentation updates.


Please be patient while this process takes place. Response times may vary depending on availability.




Coordinated disclosure.

After a fix is prepared, we aim for a coordinated disclosure:



A patched version of the affected file(s) is pushed to the repository.

A short note may be added to the README, changelog, or commit message describing the issue at a high level (without exposing exploit details).

If you wish to be credited for your responsible disclosure, please say so in your report and provide the name/handle you’d like to be credited with.




Scope

This project primarily contains:



Skript .sk files

Example configuration files (e.g. permissions.yml)

Documentation and helper text


In scope for security reporting:



Scripts that allow players to escalate their privileges unexpectedly.

Scripts that accidentally expose sensitive data (e.g. raw passwords, tokens, internal IPs) to untrusted players.

Logic flaws that allow bypassing intended protections (e.g. bypassing a lock system, abusing a command to gain unfair advantages, or crashing the server easily).

Anything that can be triggered remotely by regular players and leads to denial‑of‑service, data exposure, or privilege escalation.


Out of scope:



Issues caused solely by misconfiguration of a server outside of this repository.

Use of these scripts in unsupported environments or heavily modified forks.

General Minecraft / EaglerCraft vulnerabilities unrelated to this code.

Security problems in third‑party plugins, hosting providers, or client mods.


Handling Sensitive Data

This repository is not intended to store or process real‑world sensitive data. Still, there are a few important guidelines:



Do not hard‑code real passwords, API keys, or tokens in any scripts you contribute. Use placeholders or environment‑specific configuration instead.

Avoid logging passwords or secrets to chat or console. For example, if you create an auth or login Skript, do not send raw passwords back to staff or print them in logs.

If you discover an existing script in this repository that logs or exposes sensitive information (such as plaintext passwords), please treat it as a security issue and report it.


Best Practices for Server Owners

While not strictly part of the repository’s security, here are some basic recommendations when using these scripts on your own server:




Restrict powerful commands with permissions.

Always gate admin‑level commands (e.g. mass‑kick, bans, balance editing, lock/unlock utilities) behind appropriate permission nodes, and grant those only to trusted staff.




Test new scripts on a non‑production server first.

Before deploying new or heavily modified scripts to a live server, test them on a separate instance to make sure they do not introduce obvious exploits or crashes.




Keep backups of your scripts and configs.

This will help you quickly revert problematic changes, including ones that unintentionally open up security issues.




Keep your server and Skript versions updated when possible.

Many older builds contain bugs (and sometimes vulnerabilities) that have been fixed in newer releases. Updating reduces risk and improves stability.




Review third‑party contributions.

If you accept Skript code from other people, treat it like code review: check for hidden backdoors (e.g. secret op commands, forced operator status, or data exfiltration) before using it.




Responsible Use

By using or modifying the scripts in this repository, you agree to use them responsibly. The tools here are intended to help you:



Moderate your EaglerCraft / Minecraft server.

Add fun or useful features for your community.

Experiment and learn with simple scripting examples.


They are not intended for:



Abusing players or other servers.

Circumventing protections you do not control.

Any activity that violates applicable laws, Terms of Service, or hosting provider rules.


If you are unsure whether a use case is appropriate, err on the side of caution and ask first.



If you have any questions about this security policy, feel free to open a general GitHub issue (without sensitive details) asking for clarification.
