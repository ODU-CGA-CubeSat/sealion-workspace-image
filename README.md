# SeaLion Workspace Image

![Screenshot from 2023-07-10 22-00-18](https://github.com/ODU-CGA-CubeSat/sealion-workspace-image/assets/14095576/41ec9492-c924-40a5-a52d-85d20bca0d25)

Credits to [Oregon Marine Reserves](https://www.flickr.com/photos/ormarinereserves/16698749045/in/photostream/) for sealion wallpaper [CC BY-NC 2.0](https://creativecommons.org/licenses/by-nc/2.0/).

## Introduction

This repo provides an immutable infrastructure as code (iiac) workspace for systems architecture & development for the SeaLion CubeSat Mission.
Image currently uses an Ansible based template for [KASM Ubuntu Jammy Images](https://hub.docker.com/r/kasmweb/core-ubuntu-jammy).  The workspace is configured with the following software:

- Utilities
    - git v2.41.0 with @capsulecorplab .gitconfig
    - [Keychain](https://www.funtoo.org/Keychain) v2.8.5
    - Vim (pre-installed) with @capsulecorplab [vimrc](https://gist.github.com/capsulecorplab/495058e7a57ed8adaed3c40c80d09739#file-vimrc)
- Cross Compile Toolchain for embedded Linux
    - gcc-arm-linux-gnueabihf
    - g++-arm-linux-gnueabihf
    - gdb-multiarch
    - build-essential
    - [cmake v3.2](http://www.cmake.org/files/v3.2)
- [Keychain](https://www.funtoo.org/Keychain)
- Firefox
- [Pharo Launcher](https://github.com/pharo-project/pharo-launcher) with following [Pharo](https://pharo.org/web/) images
    - "RoassalPlayground" pre-loaded with
        - [Roassal3](https://github.com/ObjectProfile/Roassal3) v1.01b
        - [NeoCSV](https://github.com/svenvc/NeoCSV)
        - [XMLParser](https://github.com/pharo-contributions/XML-XMLParser)
        - [Roassal3Exporters](https://github://ObjectProfile/Roassal3Exporters) v1.0
- Space Mission Analysis & Design Tools
    - [General Mission Analysis Tool](https://documentation.help/GMAT/)
    - [GNU Octave](https://octave.org/)
    - [Minicom](https://launchpad.net/ubuntu/+source/minicom/2.7.1-1.1)
    - [GNU Radio Software](https://www.gnuradio.org/) 3.10.1.1
        - [gr-satellites](https://github.com/daniestevez/gr-satellites) 4.4.0
    - [GPredict](http://gpredict.oz9aec.net/)
    - [42](https://github.com/ericstoneking/42) 2024-01-02
- Python 3.10 (part of the image template) with the following packages (not part of the image template)
    - pip
    - [fprime]( 3.2.://github.com/nasa/fprime) 3.2.0
        - [fprime-tools](https://github.com/fprime-community/fprime-tools)
        - [fprime-gds](https://github.com/fprime-community/fprime-gds)
        - [fpp](https://github.com/fprime-community/fpp)
    - [JupyterLab](https://jupyter.org/)
    - [Jupyter Notebook](https://jupyter.org/)
    - [Voilà](https://voila.readthedocs.io/en/stable/index.html)
    - [Pint](https://pint.readthedocs.io/en/stable/)
    - [LinkML](https://github.com/linkml/linkml)
    - [pandas](https://pandas.pydata.org/)
    - [seaborn](https://seaborn.pydata.org/)
    - [black](https://github.com/psf/black)
- VS Code with the following extensions (note, auto-updates are disabled)
    - [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
    - [PlantUML](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)
    - [Python extension by Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- OSHW Design Tools
    - [KiCAD](https://www.kicad.org/) 7.0.10

## Requirements

1. Docker
2. Git

Notes:
- It is recommended MacOS and Windows users download [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- It is recommended to allocate at least 16gb under docker image size in your docker settings (See https://stackoverflow.com/a/65333634/12076663)
- WSL 2 users should run docker daemon with `sudo dockerd --iptables=true` (See https://stackoverflow.com/questions/40792765/docker-internet-connectivity-with-iptables-false)

## How to Use this Repo

1. Clone this repo and change directory into `sealion-workspace-image`.
1. Run `docker-compose pull` (Note: Linux users may need to prepend this command with `sudo`) to pull the published version of the workspace image.  

## Using the image locally

Once built, the image can be pushed into the Kasm server per Kasm documentation or it can be run locally on port 6901 using docker-compose.

- **Starting the image locally:** Run `docker-compose up -d`
- **Stopping the image locally:** Run `docker-compose down`

When running locally, the workspace can be accessed at https://localhost:6901 with
- **User:** `kasm_user`
- **Passwordd:** `password`
