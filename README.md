# FoundryOS &nbsp; [![bluebuild build badge](https://github.com/23sonics/foundryos-2/actions/workflows/build.yml/badge.svg)](https://github.com/23sonics/foundryos-2/actions/workflows/build.yml)

A customised image, managed with [BlueBuild](https://blue-build.org) and built on top of [Universal Blue's](https://universal-blue.org/) Fedora Kinoite base image with a selection of the packages I use daily

## Installation

### On the topic of ISOs
I will *never* host any ISOs as I don't have the resources to do this for an image that's made for my own personal use anyway. Despite this, existing experienced Linux users may try following [BlueBuild's own guide](https://blue-build.org/how-to/generate-iso/) on how to generate an ISO

### Rebasing an existing installation
If you already use Fedora Kinoite or a derivative, you could try to rebase your system. The specific method depends on your setup but the following steps should work for those using `rpm-ostree` (adapted from [BlueBuild's guide](https://blue-build.org/learn/universal-blue/#by-rebasing-from-an-existing-installation-of-fedora-atomic-or-a-derivative) (again))

Start by rebasing to an unsigned image...
```
sudo rpm-ostree rebase ostree-unverified-registry:ghcr.io/23sonics/foundryos-2:latest
sudo systemctl reboot
```

...then finish up by rebasing to the signed version:
```
sudo rpm-ostree rebase ghcr.io/23sonics/foundryos-2:latest
sudo systemctl reboot
```

> [!IMPORTANT]
> I am not liable for any issues this may cause, do not expect any support from me for this method

## Verification
These images are signed by [Sigstore's](https://www.sigstore.dev/) [cosign](https://github.com/sigstore/cosign). To verify this image's signature, download `cosign.pub` from this repository, make sure to install cosign and run the following in a terminal:
```
cosign verify --key cosign.pub ghcr.io/23sonics/foundryos-2
```
