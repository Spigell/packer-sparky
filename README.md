# DESCRIPTION

This template provides simple installation of [Sparky](https://github.com/melezhik/sparky) based on [Arch Linux](https://www.archlinux.org/) and some other dev tools.

Supported providers:
 - Virtualbox

Contains:
  - base packages
  - gcc
  - sparrow (and some additional perl modules), git
  - makepkg, yaourt
  - sparrowdo
  - sparky
  - docker
  - docker-compose

## Specification
  OS - archlinux

  architecture - x64_86

  Interface - bios

  disk - 30G

  rootpass - root/vagrant
  
  For access use vagrant/vagrant or open public key.

  For full information about box see `boxes/install.json`

  *NOTE!* The VirtualBox Guest Additions are not preinstalled! If you need shared folders please install [vbguest](https://github.com/dotless-de/vagrant-vbguest) plugin.
Or you can use [sshfs](https://github.com/dustymabe/vagrant-sshfs) plugin.
  
# Usage

1) Specify this box in Vagrantfile (spigell/sparky)

2) Put your scenarios and sparky.yml in `/srv/sparky/projects` directory.

3) See results in http://localhost:3000 

## Services

- sparkyd - main proccess (enabled).
- sparky-web - web interface for sparky (enabled).

# Instructions

For local build you must delete section about uploading to vagrant cloud. After that run:

    $ packer build arch-template.json

OR you can use `jq`

    $ jq '.["post-processors"][0] |= map(select(.type != "vagrant-cloud"))' arch-template.json | packer build -


## launch with GUI console
    
    $ packer build -var 'headless=false' arch-template.json

# See also
[Sparky](https://github.com/melezhik/sparky) - CI server based on sparrow ecosystem

[sparrow](https://github.com/melezhik/sparrow) - Used it for scripting

[ArchLinux installer](https://sparrowhub.org/info/archlinux-install) - [outthentic](https://github.com/melezhik/outthentic) plugin for installing Arch linux
