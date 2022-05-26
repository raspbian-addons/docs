# Installing

To install the repository, make sure you have an Internet connection. Install Python with `sudo apt install -y python3`, then run the following command:

```
python3 <(curl -fSsL https://scripts.raspbian-addons.org/utils/repo.py)
```
The install script will ask you which mirror you would like to use. Pick the mirror that's closest to you for the most reliable speeds. Mirror syncs happen every 24 hours.

Mirror uptime can be viewed on the [status page](https://status.raspbian-addons.org/).

<details>
<summary> Alternative installation methods </summary>
  
 First, install <code>extrepo</code>.
  
```
sudo apt install -y extrepo
```
 Then, enable the Raspbian Addons repository.
```
extrepo enable raspbian-addons
```
</details>

<details>
<summary> Uninstalling the repository </summary>

  To uninstall, execute this command. 
```
bash <(curl -fSsL https://scripts.raspbian-addons.org/utils/uninstall.sh)
```

  If you installed the repository using <code>extrepo</code>, skip the step above and simply run the following:
```
extrepo disable raspbian-addons
```
   
   Please note that uninstalling the repository will not remove any of the software installed using it.
</details>

The GPG key fingerprint is `232E 6F29 77AB D48E 5A9F  AD03 9ACB 4E70 D84B FD24`.
  
### HTTPS Connections
  
The repository is also available in https, only if you have the `apt-transport-https` package installed.
