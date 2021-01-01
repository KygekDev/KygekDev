**Note: This page is under construction. Please check back later.**

# Updating `mcpe-protocol` in PocketMine-MP Plugin Manually

Minecraft: Bedrock Edition (the Game) is constantly getting updates. However, some updates includes protocol changes. Therefore, PocketMine-MP constantly pushes updates to support latest version of the Game. To maintain plugin compatibility, PocketMine-MP uses the Game's protocol version as a standard for plugins declaring `mcpe-protocol` in `plugin.yml` to load properly. Plugins that does not match the current protocol version of the Game would show `Incompatible network protocol version` error in console and automatically disabled. PocketMine-MP updates which includes protocol changes usually bumped the minor version (`major.minor.patch`). However, not every updates of the Game break all plugins. Therefore, sometimes updating `mcpe-protocol` to match the current protocol version of the Game will work.

Knowing how to update `mcpe-protocol` in plugins is very important, because not all plugins are updated constantly to support latest PocketMine-MP version. Therefore, I made this documentation/tutorial for beginners. **If you need more information, refer to the [FAQs](https://github.com/Kygekraqmak/Kygekraqmak/blob/master/docs/update-mcpe-protocol-manually.md#faqs) section.**

## Table of Contents

## Prerequisites

- Plugin with `mcpe-protocol` declared in `plugin.yml`
- PHAR Converter ([DevTools](https://poggit.pmmp.io/p/DevTools)/[PHAR Converter](https://github.com/KygekTeam/PHAR-Converter/releases)/[phar.scer.io](https://phar.scer.io))
- PocketMine-MP server with latest version
- Basic YAML, PocketMine-MP and command line knowledge

## Converting PHAR to Directory

Before editing `plugin.yml`, you need to convert PHAR to directory. You can either use [DevTools](https://poggit.pmmp.io/p/DevTools), 
[PHAR Converter](https://github.com/KygekTeam/PHAR-Converter/releases) or [phar.scer.io](https://phar.scer.io).

#### Difficulty:
Easy: phar.scer.io\
Medium: DevTools (Preferred)\
Hard: PHAR Converter (Support us by becoming our beta tester and report bugs!)

### Converting using DevTools

1. Download [DevTools](https://poggit.pmmp.io/p/DevTools) on Poggit and install to your server
2. Install the plugin you want to convert to your server
3. Start (or restart) your server
4. Type `extractplugin {PLUGIN_NAME}` in your server console (`{PLUGIN_NAME}` is **case-sensitive**)
5. Change directory to/open `plugin_data/DevTools/{PLUGIN_NAME}_vX.X.X`

### Converting using PHAR Converter

1. Download latest release of [PHAR Converter](https://github.com/KygekTeam/PHAR-Converter/releases) or clone the repository using [Git](https://git-scm.com)
2. Open terminal or command prompt
3. Change directory to your downloaded PHAR Converter
4. Move the plugin you want to convert to the downloaded PHAR Converter directory
5. Run `pharconverter.cmd --mode=ptd --name="{PLUGIN_FILE_NAME}"` (with "" if your plugin PHAR file name contains space)
6. Change directory to/open the directory named same as your plugin file name

### Conveting using phar.scer.io

1. Visit [phar.scer.io](https://phar.scer.io)
2. Click "Select file or drop here" and browse to the plugin you want to convert to upload
3. Wait until the plugin you want to convert has been downloaded
4. Open your Downloads folder and extract the downloaded ZIP file
5. Open the extracted folder

## Editing `plugin.yml`

You've successfully converted your PHAR plugin to directory! You can see a file named `plugin.yml` inside the plugin. Now you need to edit the `plugin.yml` file.

1. Open `plugin.yml` with your favorite text editor
2. Navigate to `mcpe-protocol`
3. Add the current protocol version to `mcpe-protocol`
    - If the `mcpe-protocol` looks like these:
      ```yml
      mcpe-protocol: XXX
      ```
      Change it to these:
      ```yml
      mcpe-protocol: [XXX, {PROTOCOL_VERSION}]
      ```
    - If the `mcpe-protocol` looks like these:
      ```yml
      mcpe-protocol: [XXX, YYY]
      ```
      Change it to these:
      ```yml
      mcpe-protocol: [XXX, YYY, {PROTOCOL_VERSION}]
      ```
    - If the `mcpe-protocol` looks like these:
      ```yml
      mcpe-protocol:
      - XXX
      - YYY
      ```
      Change it to these:
      ```yml
      mcpe-protocol:
      - XXX
      - YYY
      - {PROTOCOL_VERSION}
      ```
4. Save and close the `plugin.yml` file

## Converting Directory Back to PHAR

You've successfully edited the plugin's `plugin.yml` file. Now you need to convert it back to PHAR. You can also run the plugin without converting it back to PHAR using DevTools, although it is not recommended for production servers and redistribution.

### Converting using DevTools

1. Move the plugin directory to the `plugins` directory
2. Start (or restart) your server
3. Type `makeplugin {PLUGIN_NAME}` in your server console (`{PLUGIN_NAME}` is **case-sensitive**)
4. The plugin PHAR file is located inside the `plugin_data/DevTools` directory!

### Converting using PHAR Converter

1. Open terminal or command prompt
2. Change directory to your downloaded PHAR Converter
3. Move the plugin you want to convert to the downloaded PHAR Converter directory
4. **OPTIONAL:** Open `config.yml` and set `compress` to either `gzip` or `bzip2` to save disk space
5. Run `pharconverter.cmd --mode=dtp --name="{PLUGIN_DIRECTORY_NAME}"` (with "" if your plugin directory name contains space)
6. The plugin PHAR file is located inside the PHAR Converter directory!

### Conveting using phar.scer.io

1. Select all files inside the plugin folder and compress it to ZIP
1. Visit [phar.scer.io](https://phar.scer.io)
2. Click "Select file or drop here" and browse to the plugin ZIP you want to convert to upload
3. Wait until the plugin you want to convert has been downloaded
4. The plugin PHAR file is located inside your Downloads folder!

Now you can install the plugin PHAR file to your server!

## FAQs

Q: What is a directory?\
A: Basically it is the same thing as "folders", but the term "folders" includes "virtual folders".

Q: Where can I find the current protocol version of the Game?\
A: You can find it [here](https://minecraft.gamepedia.com/Protocol_version#Bedrock_Edition_2).

Q: When should I update the `mcpe-protocol` in `plugin.yml`?\
A: When some of your plugins show `Incompatible network protocol version` error in console.

Q: Can I remove `mcpe-protocol` in `plugin.yml`?\
A: Yes you can, however it is not recommended if you're about to redistribute the plugin (for compatibility reasons).

Q: Another error occured after I updated the `mcpe-protocol` in `plugin.yml`!\
A: Please join our [Discord server](https://discord.gg/CXtqUZv) for further support (**Do not ping/DM developers and/or staffs if possible, we aren't your personal assistant**).
