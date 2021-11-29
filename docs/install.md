# Installing

To install the repository, make sure you have an Internet connection. Install Python with `sudo apt install python3`, then run the following command:

```
python3 <(curl -fSsL https://cdn.jsdelivr.net/gh/raspbian-addons/scripts@master/utils/repo.py)
```
The install script will ask you which mirror you would like to use. Pick the mirror that's closest to you for the most reliable speeds. Please note that the main mirror (apt.raspbian-addons.org) may be the most up-to-date mirror.

<details>
<summary> Uninstalling the repository </summary>

To ***uninstall***, execute this command. 
```
bash <(curl -fSsL https://cdn.jsdelivr.net/gh/raspbian-addons/scripts@master/utils/uninstall.sh)
```

</details>
