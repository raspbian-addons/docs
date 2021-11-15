# Documentation

This is the main repository documentation. If you have any questions or anything can be improved, please open an issue [here](https://github.com/raspbian-addons/raspbian-addons/issues/new).

Eventually, we'll create a formal documentation website, but for now, it's just one unified README.

### What is Raspbian Addons?

Raspbian Addons is a Debian software repository (APT repository) for awesome software that can be run on Raspberry Pies.

### What is an APT repository?

APT repositories are large collections of software packages in the form of .deb packages. In simpler terms, it's a remote directory, or server, from which your system downloads software from.

### How do APT repositories work?

1.) **Packages are downloaded to a specific directory on a server.** They can be separated by their first letter, or not, either way, they're located in the same folder.

2.) **A list of the packages is saved to the `Packages` file.** Typically, this is in a folder that's in front of the package folder. This file also contains the checksums, which are used to verify the integrity of a package being installed, as well as the directory location of the package.

3.) **The `Packages` file gets compressed with `gzip`.** This will create a file called `Packages.gz`, and is a smaller version of the package list that your system will download. This file is one step before the packages in the directory tree.

4.) **`Release`, `Release.gpg`, and `InRelease` are created.** These files are contain metadata about the repository, as well as checksums for packages. `Release.gpg` and `InRelease` are signed by the repository's secret key. These files are one step before the packages in the directory tree.

5.) **Finally, the updates are pushed to the repository.** All the newly created files replace the old ones and updates can roll out to users.

6.) **Users download and install packages from their systems.** Upon running `sudo apt update`, the Debian system will locate the .list package from `/etc/apt/sources.list` or `/etc/apt/sources.list.d`. It checks for the Release, Release.gpg, InRelease, Packages, and public key, and if they can't be located, the command will exit with an error. If successful, packages can be updated with `sudo apt upgrade`, and new ones can be installed with `sudo apt install <package name>`.

### What's the 'secret key' and 'public key'?

The repository secret key also known as the public key.. There are two parts necessary for APT: a public key, and a private key. 

The public key is installed into the user's APT keyring locally on their system, and is used to verify the integrity of the downloaded packages. In Raspbian Addons, the public key is [KEY.gpg](https://osdn.net/projects/raspbian-addons/storage/KEY.gpg)

The private key is also known as the secret key, and is used to write, or add, packages to the repository, using an awesome encryption engine called `gpg`. Only the repository maintainers have access to this key.

### Common Issues

- **"This repository does not have a Release or InRelease file."**

	To fix, just uninstall the repository and then re-install it using the instructions above. The format of the repository was changed on 8/22/21, due to which this error is caused.
	(Or, if you're feeling adventurous, edit the `rpirepo.list` file in /etc/apt/sources.list.d/, and change the ending from `raspbian-addons/debian buster main` to `raspbian-addons/debian/ /`)

- **"E: Unable to locate package packagename"**

	This error can happen due to one of the following reasons:
	- The package cannot be installed on the system's architecture, for example, if you're trying to install `arm64` software on an `armhf` machine, this error will occur.
	- The package does not exist in the repository. Running `sudo apt-get update` may fix this, if it doesn't, make sure the software is on the [list of packages](https://apt.raspbian-addons.org/debian/pool/).

- **"package: Dependency: package2 but it will not be installed"**

	This is an extremely common error and usually it's an easy fix. Just add the dependency that's needed for the package to the install command. In this example, the install command will be `sudo apt install package package2`.

- **"Dependency: package but unable to install it"**

	If you're encountering this error, chances are others are too. Open an issue [here](https://github.com/raspbian-addons/raspbian-addons/issues/new), and we'll take a look into it.

If you're having any other issues or the methods to fix an issue listed here aren't working, be sure to open an issue report on the raspbian-addons repository, not the software creator's repository.

### Running a repository speed test

Testing the speed of each of the mirrors to see which one is best for you can be done with this script.

```
bash <(curl -fSsL https://cdn.jsdelivr.net/gh/raspbian-addons/scripts@master/utils/speedtest.sh)
```

### Package List

This area contains a description of each application in the repository.

All the packages can be found [here](https://apt.raspbian-addons.org/debian/pool/).

| Package Name | Package Description | Project Homepage |
| ------------- | ------------- | ------------- |
| adoptopenjdk | Prebuilt OpenJDK binaries | https://adoptopenjdk.net/  |
| alacritty | Cross-platform OpenGL terminal emulator | https://github.com/alacritty/alacritty |
| albert | A fast and flexible keyboard launcher | https://github.com/albertlauncher/albert |
| ali | Generate HTTP load and plot the results in real-time | https://github.com/nakabonne/ali |
| amazon-corretto | No-cost, multiplatform, production-ready distribution of the Java Development Kit. | https://corretto.aws |
| amiberry | Optimized Amiga emulator for the Raspberry Pi and other ARM boards | https://amiberry.com |
| appimagelauncher | Helper application for running and integrating AppImages | http://github.com/TheAssassin/AppImageLauncher |
| archivebox | Open-source self hosted web archiving. | https://github.com/ArchiveBox/ArchiveBox |
| balena-etcher-electron | Flash OS images to SD card and USB drives safely and easily. | https://github.com/balena-io/etcher |
| bat | a cat clone with wings. | https://github.com/sharkdp/bat |
| bleachbit | Clean your system and free disk space. | https://bleachbit.org |
| blockbench | Free modern model editor for low-poly and boxy models with pixel art textures. | https://github.com/JannisX11/blockbench |
| bashtop | Linux command-line resource manager. | https://github.com/aristocratos/bashtop |
| blockpi | visual programming editor for Raspberry Pi | https://github.com/alienzhangyw/BlockPi |
| box64 | Linux Userspace x86_64 Emulator with a twist, targeted at ARM64 Linux devices | https://github.com/ptitSeb/box64 |
| box86 | Linux Userspace x86 emulator with a twist. | https://github.com/ptitSeb/box86 |
| bpytop | Linux resource monitor written in Python. | https://github.com/aristocratos/bpytop |
| browsh | Fully-modern text-based web browser | https://github.com/browsh-org/browsh |
| bulky | Bulk Renamer | https://github.com/linuxmint/bulky |
| caddy | Fast multi-platform web server with https | https://github.com/caddyserver/caddy |
| cbonsai | grow bonsai trees in your terminal | https://gitlab.com/jallbrit/cbonsai |
| cfetch | simple system information tool for linux. | https://github.com/cliegargo/cfetch |
| cherrytree | Feature rich note-taking application | https://github.com/giuspen/cherrytree |
| clamtk | ondemand virus scanner for Linux | https://github.com/dave-theunsub/clamtk |
| clementine | modern music player and library organizer for Linux | https://github.com/clementine-player/Clementine |
| cloudflared | Argo Tunnel client | https://github.com/cloudflare/cloudflared |
| code-server | VS Code in the browser | https://github.com/cdr/code-server |
| codium | binary releases of VSCode without telemetry and tracking | https://github.com/VSCodium/vscodium |
| foliate | modern GTK ebook reader | https://github.com/johnfactotum/foliate |
| conky-manager | manage all your Conky theme | https://github.com/teejee2008/conky-manager |
| croc | easily and securely send things from one computer to another | https://github.com/schollz/croc |
| deskreen | turn any device with a web browser into a second screen | https://github.com/pavlobu/deskreen |
| dino | modern gtk-based XMPP client | https://github.com/dino/dino |
| docker-ctop | top-like interface for container metrics | https://github.com/bcicen/ctop |
| drawing | simple image editor for Linux | https://github.com/maoschanz/drawing |
| duckstation | PlayStation 1 emulator | https://github.com/stenzek/duckstation |
| duf | Disk usage monitoring utility | https://github.com/muesli/duf |
| elasticsearch | free and open search engine | https://github.com/elastic/elasticsearch |
| electron-fiddle | Create and play with Electron experiments | https://github.com/electron/fiddle |
| fancy-cursor-themes | Some extra cursor themes for Linux distributions | https://github.com/ryanfortner/cursor-themes |
| figma-linux | interface design tool based in the browser | https://github.com/Figma-Linux/figma-linux |
| firefox (currently broken) | popular open-source web browser backed by Mozilla | https://www.mozilla.org/en-US/firefox/new/ |
| flameshot | Powerful yet simple screenshot software | https://github.com/flameshot-org/flameshot |
| fonts-noto-color-emoji | color emoji font | none |
| fonts-twemoji-svginot | emoji font | none |
| freecad | free and open source parametric modeler | https://github.com/FreeCAD/FreeCAD |
| freetube | Private YouTube client | https://freetubeapp.io/ |
| fzf | command-line fuzzy finder | https://github.com/junegunn/fzf |
| gh | GitHub's official command line tool | https://github.com/cli/cli |
| gitea | Painless self-hosted Git solution | https://github.com/go-gitea/gitea |
| glab | open-source GitLab command-line tool | https://github.com/profclems/glab |
| glmark2 | openGL 2.0 and ES 2.0 benchmark tool | https://github.com/glmark2/glmark2 |
| goreleaser | Deliver Go binaries as fast as possible | https://github.com/goreleaser/goreleaser |
| hyper | a terminal built on web technologies. | https://github.com/vercel/hyper |
| hypnotix | an M3U IPTV player | https://github.com/linuxmint/hypnotix |
| influxdb | Scalable datastore for metrics, events, and real-time analytics | https://github.com/influxdata/influxdb |
| v2raya | A Linux web GUI client of Project V which supports V2Ray, Xray, SS, SSR, Trojan and Pingtunnel | https://github.com/v2rayA/v2rayA |
| ipscan | fast and friendly network scanner | https://github.com/angryip/ipscan |
| ish | A simple shell written in C | https://github.com/Itai-Nelken/ish |
| kdiskmark | simple disk benchmarking tool | https://github.com/JonMagon/KDiskMark |
| keepassx | cross-platform password safe | https://github.com/keepassx/keepassx |
| koreader | Ebook reader application supporting many different ebook formats | https://github.com/koreader/koreader |
| libhalf-life | runtime files and desktop entry for running half-life on a raspberry pi. needs full data files to run | https://github.com/jmcerrejon/PiKISS/blob/master/scripts/games/half-life.sh |
| lightpad | Lightweight, simple, and powerful application launcher. | https://github.com/libredeb/lightpad |
| linuxcnc-uspace | LinuxCNC controls CNC machines. It can drive milling machines, lathes, 3d printers, laser cutters, plasma cutters, robot arms, hexapods, and more. | https://github.com/LinuxCNC/linuxcnc |
| log2ram | put log in a ram folder | https://github.com/azlux/log2ram |
| logo-ls | modern ls command alternative written in Go | https://github.com/Yash-Handa/logo-ls |
| lutris | Game launcher: desktop client | https://github.com/lutris/lutris |
| lx-music-desktop | Music player made with Electron | https://github.com/lyswhut/lx-music-desktop |
| macintosh.js | Virtual macintosh running System 8 in electron | https://github.com/felixrieseberg/macintosh.js/ |
| makedeb | modern packaging tool for Debian archives | https://github.com/makedeb/makedeb |
| min | Fast, minimal, and private web browser | https://github.com/minbrowser/min |
| minikube | Run Kubernetes locally | https://github.com/kubernetes/minikube |
| msopenjdk-16 | Microsoft's build of OpenJDK | https://www.microsoft.com/openjdk |
| musikcube | a cross-platform, terminal-based music player, audio engine, metadata indexer, and server in c++ | https://github.com/clangen/musikcube |
| n | Node version management | https://github.com/tj/n |
| nomacs | Free image viewer | https://github.com/nomacs/nomacs |