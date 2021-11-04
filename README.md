# Documentation

This is the main repository documentation. If you have any questions or anything can be improved, please open an issue [here](https://github.com/raspbian-addons/raspbian-addons/issues/new).

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

- "This repository does not have a Release or InRelease file."

	To fix, just uninstall the repository and then re-install it using the instructions above. The format of the repository was changed on 8/22/21, due to which this error is caused.

	(Or, if you're feeling adventurous, edit the `rpirepo.list` file in /etc/apt/sources.list.d/, and ***change the ending from `raspbian-addons/debian buster main` to `raspbian-addons/debian/ /`***)

If you're having any other issues or the methods to fix an issue listed here aren't working, be sure to open an issue report on ***this*** github repo and not on the creators of the app's repo (unless you're having an issue with a specific app).

### Running a repository speed test

Testing the speed of each of the mirrors to see which one is best for you can be done with this script.

```
bash <(curl -fSsL https://cdn.jsdelivr.net/gh/raspbian-addons/scripts@master/utils/speedtest.sh)
```