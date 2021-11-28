# Repository Scripts

Raspbian Addons uses [shell scripts](https://en.wikipedia.org/wiki/Shell_script), or Unix command-line programs, to update its packages. How does it do this?

Every 24 hours, the virtual machine running the repository will download [the autoupdate script](https://github.com/ryanfortner/au-sh). The VM makes the script executable with a `chmod +x au.sh`, and proceeds to execute it.
