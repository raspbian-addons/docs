# Installing

To install the repository, make sure you have an Internet connection. Install Python with `sudo apt install -y python3`, then run the following command:

```
python3 <(curl -fSsL https://cdn.jsdelivr.net/gh/raspbian-addons/scripts@master/utils/repo.py)
```
The install script will ask you which mirror you would like to use. Pick the mirror that's closest to you for the most reliable speeds. Please note that the main repository (apt.raspbian-addons.org) may be the most up-to-date.

<details>
<summary> An alternative to add the main repository </summary>
  
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

  To <i><strong>uninstall</strong></i>, execute this command. 
```
bash <(curl -fSsL https://cdn.jsdelivr.net/gh/raspbian-addons/scripts@master/utils/uninstall.sh)
```

  If you installed the repository using <code>extrepo</code>, skip the step above and simply run the following:
```
extrepo disable raspbian-addons
```
            
</details>

The GPG key fingerprint is `232E 6F29 77AB D48E 5A9F  AD03 9ACB 4E70 D84B FD24`.
  
### HTTPS Connections
  
The repository is also available in https, only if you have the `apt-transport-https` package installed.
