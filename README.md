# CraftPriority — downloads

An [AsaApi](https://github.com/ArkServerApi/AsaApi) plugin for **ARK: Survival Ascended** dedicated servers:
at shared crafting stations, **smaller crafting jobs go first**. A big job finishes the unit it is on, lets
the smaller job through, then carries on where it left off, with no progress lost. Costs, Cancel Queue, power
loss and the queue limit all behave exactly as they do in unmodified ASA.

This repository holds the release files only. It has no source code in it.

Full guide: [romoslayer.com/docs/craft-priority](https://romoslayer.com/docs/craft-priority/overview)

## Download

**[Download CraftPriority.zip](https://github.com/Romoslayer/CraftPriority-Releases/releases/latest/download/CraftPriority.zip)**
— the latest release. Requires AsaApi V2.11 or later.

The zip holds one `CraftPriority` folder: the plugin, `PluginInfo.json`, `config.json` and `LICENSE.txt`.
Each release lists the zip's SHA-256 checksum, so you can check that your download matches.

## Install

1. Stop the server.
2. Copy the `CraftPriority` folder into `ShooterGame/Binaries/Win64/ArkApi/Plugins/`.
3. Start the server. The ArkApi log shows `CraftPriority <version> loaded.`

It runs entirely on the server, so players install nothing. Install it on every map where you want it.

If the log says `CraftPriority is NOT active`, something the plugin relies on has changed, for example after
an ARK update. Crafting then behaves exactly like vanilla until the plugin is updated.

**Updating while the server runs:** copy the new `CraftPriority.dll` into the plugin folder as
`CraftPriority.dll.ArkApi`. AsaApi saves the world and reloads the plugin within about a minute.

**Do not use `plugins.unload CraftPriority`.** It can crash the server. Update as above, or stop the server.

**Uninstall:** stop the server and delete the `CraftPriority` folder.

## Settings

`config.json` in the plugin folder:

```jsonc
{
    // true  = smaller crafting jobs go first
    // false = crafting stations behave like unmodified ASA
    "EnableCraftPriority": true,

    // Which jobs go first:
    // "Quantity"          = fewest items queued first (default)
    // "QuantityThenSpeed" = fewest items queued first; if equal, the faster craft goes first
    // "Time"              = least total crafting time first (all items queued in the job)
    "PriorityBy": "Quantity",

    // true  = log every queue change (for testing; busy servers log a lot)
    // false = log only startup and errors
    "EnableDebugLogging": false
}
```

Apply changes with `CraftPriority.Reload` from the admin console or over RCON.

## Support

[romoslayer.com/support](https://romoslayer.com/support)

## Licence

Free to download and run on ARK: Survival Ascended servers you operate or administer. Modifying, decompiling
or redistributing it is not allowed. Copyright © 2026 Romoslayer, all rights reserved. See [LICENSE](LICENSE).
