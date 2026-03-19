# FoundryOS &nbsp; [![bluebuild build badge](https://github.com/23sonics/foundryos-2/actions/workflows/build.yml/badge.svg)](https://github.com/23sonics/foundryos-2/actions/workflows/build.yml)

 Customised images, managed with [BlueBuild](https://blue-build.org) and built on top of [Universal Blue's](https://universal-blue.org/) base images with a selection of the packages I use daily plus a choice between KDE Plasma and GNOME desktops

## Installation
> [!WARNING]
> I will not provide support for these images to anyone other than myself. If you want to try to install this image anyway, proceed at your own risk.

### On the topic of ISOs
I will *never* host any ISOs as I don't have the resources to do this for images made for my own personal use anyway. Despite this, existing experienced Linux users may try following [BlueBuild's own guide](https://blue-build.org/how-to/generate-iso/) on how to generate an ISO, although this is not guaranteed to work properly

### Rebasing an existing installation
If you already use Fedora Silverblue or Kinoite, or a derivative of one, you could try to rebase your system. The specific method depends on your setup but the following steps should work for those using `rpm-ostree` (adapted from [BlueBuild's guide](https://blue-build.org/learn/universal-blue/#by-rebasing-from-an-existing-installation-of-fedora-atomic-or-a-derivative) (again))

Start by rebasing to an unsigned image, replace `[variant]` with `2` for Plasma or `gnome` for GNOME...
```
sudo rpm-ostree rebase ostree-unverified-registry:ghcr.io/23sonics/foundryos-[variant]:latest
sudo systemctl reboot
```

...then finish up by rebasing to the signed version:
```
sudo rpm-ostree rebase ghcr.io/23sonics/foundryos-[variant]:latest
sudo systemctl reboot
```

## Verification
These images are signed by [Sigstore's](https://www.sigstore.dev/) [cosign](https://github.com/sigstore/cosign). To verify an image's signature, download `cosign.pub` from this repository, make sure to install cosign and run the following in a terminal:
```
cosign verify --key cosign.pub ghcr.io/23sonics/foundryos-[variant]
```
