# SeaLion Mission Workspace (Kasm Image)

## Introduction

This repo provides a workspace for the SeaLion team to work on GNU Radio, Flight Software, & Ground Station based on the [Ansible based template for KASM Ubuntu Focal Images](https://github.com/j-simmons-phd/kasm-core-focal-template) template provided by @j-simmons-phd.  The workspace is configured with the following software:

- Cross Compile Toolchain for embedded Linux
  - gcc-arm-linux-gnueabihf
  - g++-arm-linux-gnueabihf
  - gdb-multiarch
  - build-essential
  - [cmake v3.2](http://www.cmake.org/files/v3.2)
- git cli
- [git lfs](https://git-lfs.github.com/)
- [Keychain](https://www.funtoo.org/Keychain)
- Chrome
- Eclipse IDE for Embedded C/C++ (2019-03 release)
- [General Mission Analysis Tool](https://documentation.help/GMAT/)
- [GNU Octave](https://octave.org/)
- [GNU Radio Software](https://www.gnuradio.org/)
- [GPredict](http://gpredict.oz9aec.net/)
- Python 3.8.x (part of the image template) with the following packages (not part of the image template)
    - pip
    - [fprime-tools](https://github.com/fprime-community/fprime-tools)
    - [fprime-gds](https://github.com/fprime-community/fprime-gds)
    - [JupyterLab](https://jupyter.org/)
    - [Jupyter Notebook](https://jupyter.org/)
    - [Voilà](https://voila.readthedocs.io/en/stable/index.html)
    - [Pint](https://pint.readthedocs.io/en/stable/)
- VS Code with the following extensions (note, auto-updates are disabled)
    - [Python extension by Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

## Requirements

1. Docker
2. Git

Notes:
- It is recommended MacOS and Windows users download [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- It is recommended to allocate at least 16gb under docker image size in your docker settings (See https://stackoverflow.com/a/65333634/12076663)

## WSL2 audio configuration

WSL2 users will need to add the following line to `~/.bashrc` in the kasm workspace:

```bash
export PULSE_SERVER=tcp:$(grep nameserver /etc/resolv.conf | awk '{ print $2 }')
```

See http://sites.music.columbia.edu/brad/osx-windows-new-RTcmixes/wsl2-RTcmix.html for more details.

## How to Use this Repo

1. Clone this repo and change directory into `kasm-sealion-workspace`.
1. Run `docker-compose pull` (Note: Linux users may need to prepend this command with `sudo`) to pull the published version of the workspace image.  

## Using the image locally

Once built, the image can be pushed into the Kasm server per Kasm documentation or it can be run locally on port 6901 using docker-compose.

- **Starting the image locally:** Run `docker-compose up -d`
- **Stopping the image locally:** Run `docker-compose down`

When running locally, the workspace can be accessed at https://localhost:6901 with
- **User:** `kasm_user`
- **Passwordd:** `password`
