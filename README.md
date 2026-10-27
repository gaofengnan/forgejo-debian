![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/gaofengnan/forgejo-debian/total)
![GitHub Downloads (all assets, latest release)](https://img.shields.io/github/downloads/gaofengnan/forgejo-debian/latest/total)
![GitHub Release](https://img.shields.io/github/v/release/gaofengnan/forgejo-debian)
![GitHub Release Date](https://img.shields.io/github/release-date/gaofengnan/forgejo-debian)

<h1>
   <p align="center">
     <a href="https://forgejo.org/"><img src="https://github.com/gaofengnan/forgejo-debian/blob/main/forgejo-logo.png" alt="Forgejo Logo" width="128" style="margin-right: 20px"></a>
     <a href="https://www.debian.org/"><img src="https://github.com/gaofengnan/forgejo-debian/blob/main/debian-logo.png" alt="Debian Logo" width="104" style="margin-left: 20px"></a>
     <br>Forgejo for Debian
   </p>
</h1>
<p align="center">
  Forgejo is a self-hosted lightweight software forge. Easy to install and low maintenance, it just does the job.
</p>

# Forgejo for Debian

> Fork of [dariogriffo/forgejo-debian](https://github.com/dariogriffo/forgejo-debian) (MIT); the original packaging is by Dario Griffo. Served at [deb.gaofn.xyz](https://deb.gaofn.xyz) for Debian 12 (bookworm) and 13 (trixie).

This repository contains build scripts to produce the _unofficial_ Debian packages
(.deb) for [Forgejo](https://forgejo.org/) hosted at [deb.gaofn.xyz](https://deb.gaofn.xyz)

Currently supported Debian distros are:
- Bookworm
- Trixie
- Sid

Currently supported Ubuntu distros are:
- Jammy
- Noble
- Questing
- Resolute

Supported architectures: **amd64**, **armhf**, **arm64**

This is an unofficial community project to provide a package that's easy to
install on Debian/Ubuntu. If you're looking for the Forgejo source code, see
[codeberg.org/forgejo/forgejo](https://codeberg.org/forgejo/forgejo).

## Install/Update

### The Debian way

```sh
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.gpg -o /etc/apt/keyrings/deb.gaofn.xyz.gpg
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.sources -o /etc/apt/sources.list.d/deb.gaofn.xyz.sources
# Debian 12 (bookworm): fetch deb.gaofn.xyz-bookworm.sources instead
sudo apt update
sudo apt install -y forgejo
```

### Manual Installation

1. Download the .deb package for your distribution and architecture from the
   [Releases](https://github.com/gaofengnan/forgejo-debian/releases) page.
2. Install the downloaded .deb package:

```sh
sudo dpkg -i <filename>.deb
```

## Post-installation

After installing the package, complete the Forgejo setup:

1. Start the service:
   ```sh
   sudo systemctl start forgejo
   ```
2. Open `http://localhost:3000` in your browser and follow the initial configuration wizard.
3. After completing the web-based setup, enable Forgejo on boot:
   ```sh
   sudo systemctl enable forgejo
   ```

The package automatically:
- Creates the `git` system user and group
- Creates `/var/lib/forgejo` (data directory, owned by `git:git`, mode `750`)
- Creates `/etc/forgejo` (config directory, owned by `root:git`, mode `770`)
- Installs the systemd service file

## Updating

To update to a new version, follow any of the installation methods above. There is no need to uninstall the old version first; it will be updated correctly.

## Roadmap

- [x] Produce .deb packages on GitHub Releases
- [x] Support amd64, armhf, arm64 architectures
- [x] Post-install setup (user, directories, systemd service)
- [ ] Set up a debian mirror for easier updates

## Disclaimer

This repo is not open for issues related to Forgejo itself. This repo is only for _unofficial_ Debian/Ubuntu packaging.
