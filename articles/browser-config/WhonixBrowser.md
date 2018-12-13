Using Whonix's i2p Browser Launching Scripts on Debian-Based GNU/Linux
======================================================================

**This guide is intended for users who are aware of the implications of using**
**third-party repositories on their Debian-based Linux PC's.** In particular,
Whonix is designed to pro-actively prevent certain kinds of attacks from
affecting the user, and their packages sometimes overwrite things like hosts
files and such with versions suitable for the Whonix threat model. While I
currently use the following packages successfully on both Debian and Ubuntu
Linux at this time, I cannot guarantee that they will work for everyone's
specific configuration.

Installation/Use:
-----------------

First, you will need to install the Whonix package signing key with apt-key add.
This will allow apt to vet the source of the new packages to confirm that they
are indeed from the Whonix project.

```sh
sudo apt-key --keyring /etc/apt/trusted.gpg.d/whonix.gpg adv --keyserver hkp://ipv4.pool.sks-keyservers.net:80 --recv-keys 916B8D99C38EAF5E8ADC7A2A8D66066A2EEACCDA
```

Next, you will need to add the Whonix stretch-testers repository to your package
sources.

```sh
echo 'deb http://deb.whonix.org stretch-testers main' | tee /etc/apt/sources.list.d/whonix-testing.list # apt-transport-* season to taste
```

Update your packages to see what is available from the new package source.

```sh
sudo apt-get update
```

Install the tb-starter package and it's dependencies.

```sh
sudo apt-get install tb-starter
```

Finally, you need to add the following lines to the bottom of
/etc/i2pbrowser.d/31\_i2p\_default.conf.

```sh
TOR_HIDE_UPDATE_CHECK_UI=1
TOR_NO_DISPLAY_NETWORK_SETTINGS=1
TOR_HIDE_BROWSER_LOGO=1
TOR_SKIP_LAUNCH=1
TOR_SKIP_CONTROLPORTTEST=1
```

Once you have tb-starter installed and your configuration prepared, you can
launch your new Tor Browser for i2p by running

```sh
i2pbrowser
```

In a terminal.
