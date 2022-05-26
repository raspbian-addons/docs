# Repository Scripts

Raspbian Addons uses [shell scripts](https://en.wikipedia.org/wiki/Shell_script), or Unix command-line programs, to update its packages every 24 hours. How does it do this?

- First, the VM hosting the repository will download [the autoupdate script](https://github.com/raspbian-addons/scripts/blob/master/au.sh) and make it executable, in other words, make it recognizable as a program by the system.
- The script contains special lines which tell the VM what to download and where to put the file. First, the variables are defined, telling the system what directories to remember for later as well as other values.
- Next, the system contacts the [GitHub API](https://api.github.com/), searching for the latest version of a package. Once a value is fetched, the value is checked against the last saved version, and if they're not equal, the package will continue to be downloaded.
- If no errors have occured thus far, the system will continue, replacing the old package with the newly downloaded package. The process repeats until all packages have been downloaded.
- Then, packages are written to the repository using `gpg`. You can read more about the write process [here](https://docs.raspbian-addons.org/about/how-does-it-work/), or, if you want to create a repository for yourself, see [this blog post](https://ryanfortner.github.io/blog/2021/12/10/create-apt-repo.html)

The scripts used for the repository are completely open-source and can be found at the following page:

[https://github.com/raspbian-addons/autoupdate](https://github.com/raspbian-addons/autoupdate)

We are open to any feedback on our scripts. Feel free to open a PR if you'd like to contribute!
