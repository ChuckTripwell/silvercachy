# SilverCachy &nbsp; [![bluebuild build badge](https://github.com/tapir/silvercachy/actions/workflows/build.yml/badge.svg)](https://github.com/tapir/silvercachy/actions/workflows/build.yml)

An `atomic` image based on Fedora Silverblue. I have 2 variants: `silvercachy-desktop` and `silvercachy-laptop`. It's pretty much the same except the desktop version has the`nvidia` drivers included and the laptop version uses `scx_bpfland` scheduler in power saving mode by default. According to my tests this scheduler is super good for battery operated computers. Laptop version also has some settings to fix sleeping while docked.

Both images are completely barebones and only come with a terminal and an app store so that people can install whatever they want. I removed all non-flatpak GUI apps.
Only opiniated defaults are `AppIndicator` Gnome extension being installed by default and `toolbox` being removed as I think people should just use `distrobox` instead.

## Installation

- Disable `secureboot` from BIOS and boot to an atomic distro
- Switch to the latest image of `desktop` or `laptop`
  ```
  bootc switch ghcr.io/tapir/silvercachy-desktop:latest
  systemctl reboot
  ```
- Accept MOK key enrollment with password `scachy`
- Enable `secureboot` back

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/tapir/silvercachy-desktop
```