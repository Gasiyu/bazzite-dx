# bazzite-dx &nbsp; [![build-ublue](https://github.com/Gasiyu/bazzite-dx/actions/workflows/build.yml/badge.svg)](https://github.com/Gasiyu/bazzite-dx/actions/workflows/build.yml)

This is my custom Bazzite image that tries to add all the development capabilities from the Bluefin/Aurora DX images.
It includes docker, podman, vscode, etc... to get you started coding with devcontainers faster as advertised by the Bluefin project.

### Disclaimer  
These images as provided as is and are considered in alpha state!

## Desktop Environment
This image comes with GNOME Desktop Environment:
- **bazzite-dx-gnome-nvidia-open** based on **bazzite-gnome-nvidia-open**, runs GNOME with **bluefin-dx** layered on top

## Installation

> **Warning**  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First choose the flavor of the image you'd like to install (**bazzite-dx-gnome-nvidia-open**)

- Then rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/Gasiyu/bazzite-dx-gnome-nvidia-open:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/Gasiyu/bazzite-dx-gnome-nvidia-open:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/Gasiyu/bazzite-dx
```
