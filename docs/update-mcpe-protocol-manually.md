**Note: This page is under construction. Please check back later.**

# Updating `mcpe-protocol` in PocketMine-MP Plugin Manually

Minecraft: Bedrock Edition (the Game) is constantly getting updates. However, some updates includes protocol changes.
Therefore, PocketMine-MP constantly pushes updates to support latest version of the Game.
To maintain plugin compatibility, PocketMine-MP uses the Game's protocol version as a standard for plugins declaring `mcpe-protocol` in `plugin.yml` for the plugins to load.
Plugins that does not match the current protocol version of the Game would show `Incompatible network protocol version` error in console and automatically disabled.
PocketMine-MP updates which includes protocol changes usually bumped the minor version (`major.minor.patch`).
However, not every updates of the Game break all plugins. Therefore, sometimes updating `mcpe-protocol` to match the current protocol version of the Game will work.

Knowing how to update `mcpe-protocol` in plugins is very important, because not all plugins are updated constantly to support latest PocketMine-MP version.
Therefore, I made this documentation/tutorial just for you. If you need more information, refer to the [FAQs] section.

## Table of Contents

## Prerequisites

## FAQs

Q: Where can I find the current protocol version of the Game?\
A: You can find it [here](https://minecraft.gamepedia.com/Protocol_version#Bedrock_Edition_2).

Q: When should I update the `mcpe-protocol` in `plugin.yml`?\
A: When some of your plugins show `Incompatible network protocol version` error in console.

Q: Can I remove `mcpe-protocol` in `plugin.yml`?\
A: Yes you can, but it is not recommended if you're about to redistribute the plugin (for compatibility reasons).

Q: Another error occured after I updated the `mcpe-protocol` in `plugin.yml`!\
A: Please join our [Discord server](https://discord.gg/CXtqUZv) for further support (**Do not ping/DM developers and/or staffs if possible, we aren't your personal assistant**).
