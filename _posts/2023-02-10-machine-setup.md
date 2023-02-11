---
layout: post
title:  "Setting up a new Mac"
date:   2023-02-10 21:22:54 +0000
categories: tech
---
Ok, so I've set up my Macs three times in the space of four weeks. I thought it best to write down what preferences I like and I can revisit this at a later date when I forget what to do...

# Bash > ZSH, ohMyZsh & Brew
ZSH isn't for everyone but I like the Git plugin to let me know where I am when I'm working in the terminal. And colours. The more the merrier.
1. Install [homebrew](https://brew.sh/), the Mac package manager
2. Grab Xcode from the App Store.
3. Install ZSH and other dependancies while we're here...
  ```sh
    brew install zsh \
    solargraph \
    asdf \
    ffmpeg \
    lazygit \
    webp \
    wget \
    youtube-dl \
    macfuse \
    monitorcontrol \
    appcleaner \
  ```
4. Install [ohMyZsh](https://ohmyz.sh/)
5. Install other apps from the App Store

# Apps
- 1Password
- Alfred
- Backblaze
- Bartender
- Beeper
- Carbon Copy Cloner
- Charles
- Divvy
- Dropover
- Fantastical
- GPG Keychain
- ImageOptim
- iStat Menus
- Little Snitch
- NetNewsWire
- Notion
- Nova
- RapidAPI
- ResilioSync
- Sim Genie
- Sip
- Tailscale
- Things
- Transmit
- VLC

# Other files
### Update Hosts file
I really, really hate the fact the internet has become a place where it needs to sustain itself with ads and other bad actors. [Dan Pollock](https://someonewhocares.org/hosts/) keeps a fairly up-to-date hosts file you can drop into `/etc/hosts` which creates a local feedback loop to block lots of these web nasties. I think might go a bit overboard with Little Snitch (blocking port 80), a PiHole and an AdGuard extension. Sometimes redirections are bad and Little Snitch has to be toggled, generally I see fewer ads!
```sh
  > sudo nano /etc/hosts
```
