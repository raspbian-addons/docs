# Common Issues

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

If you're having any other issues, or the methods to fix an issue listed here aren't working, be sure to open an issue report on the raspbian-addons repository, _not_ the software creator's repository.