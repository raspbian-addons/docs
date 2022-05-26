# Secret and Public Keys

The repository needs two keys in order to be secure. There are two parts necessary for APT: a public key, and a private key. 

The public key is installed into the user's APT keyring locally on their system, and is used to verify the integrity of the downloaded packages. In Raspbian Addons, the public key is [KEY.gpg](https://osdn.net/projects/raspbian-addons/storage/KEY.gpg)

The private key is also known as the secret key, and is used to write, or add, packages to the repository, using an encryption engine called `gpg`. Only the repository maintainers have access to this key.