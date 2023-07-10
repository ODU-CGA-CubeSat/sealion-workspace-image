# SeaLion Workspace Image

## Introduction

This repo provides an immutable infrastructure as code (iiac) workspace for systems architecture & development for the SeaLion CubeSat Mission.
Base image currently usest the [Ansible based template for KASM Ubuntu Focal Images](https://github.com/j-simmons-phd/kasm-core-focal-template) template provided by @j-simmons-phd.  The workspace is configured with the following software:

- Utilities
    - git v2.41.0 with @capsulecorplab .gitconfig
    - [Keychain](https://www.funtoo.org/Keychain) v2.8.5
    - Vim (pre-installed) with @capsulecorplab [vimrc](https://gist.github.com/capsulecorplab/495058e7a57ed8adaed3c40c80d09739#file-vimrc)
- Artifact Generators
    - [Pandoc](https://pandoc.org/) v2.17.0.1
    - [TeX Live](https://www.tug.org/texlive/) v2019 to enable PDF support in Pandoc
    - [yq](https://mikefarah.gitbook.io/yq/) v4.20.2
    - [PlantUML](https://plantuml.com/)
        - JDK v11
        - Graphviz 2.50 (built from source)
    - [AsciiDoctor](https://asciidoctor.org/) v2.0.17 with PlantUML and PDF support
- Cross Compile Toolchain for embedded Linux
    - gcc-arm-linux-gnueabihf
    - g++-arm-linux-gnueabihf
    - gdb-multiarch
    - build-essential
    - [cmake v3.2](http://www.cmake.org/files/v3.2)
- [Keychain](https://www.funtoo.org/Keychain)
- Firefox
- [Pharo](https://pharo.org/)
- [General Mission Analysis Tool](https://documentation.help/GMAT/)
- [GNU Octave](https://octave.org/)
- [Minicom](https://launchpad.net/ubuntu/+source/minicom/2.7.1-1.1)
- [GNU Radio Software](https://www.gnuradio.org/)
- [GPredict](http://gpredict.oz9aec.net/)
- Python Based Tools
    - Jupyter Lab
    - Juptyer Notebook
    - Voila
    - Pint
- Python 3.10 (part of the image template) with the following packages (not part of the image template)
    - pip
    - [fprime-tools](https://github.com/fprime-community/fprime-tools)
    - [fprime-gds](https://github.com/fprime-community/fprime-gds)
    - [JupyterLab](https://jupyter.org/)
    - [Jupyter Notebook](https://jupyter.org/)
    - [Voilà](https://voila.readthedocs.io/en/stable/index.html)
    - [Pint](https://pint.readthedocs.io/en/stable/)
    - [LinkML](https://github.com/linkml/linkml)
- VS Code with the following extensions (note, auto-updates are disabled)
    - [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
    - [PlantUML](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)
    - [Python extension by Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- OSHW Design Tools
    - [KiCAD](https://www.kicad.org/) 7.0.5

## Requirements

1. Docker
2. Git

Notes:
- It is recommended MacOS and Windows users download [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- It is recommended to allocate at least 16gb under docker image size in your docker settings (See https://stackoverflow.com/a/65333634/12076663)

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
