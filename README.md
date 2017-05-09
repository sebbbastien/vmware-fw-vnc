# ESX VIB for the VNC fw. rules

## Generate

```
vagrant plugin install vagrant-sshfs
vagrant up && vagrant destroy -f
```

Generated VIB is in the current working directory.

## Deploy

### Install

```
esxcli software acceptance set --level=CommunitySupported

esxcli software vib install -v $PWD/fw-vnc.vib
# or
esxcli software vib install -d $PWD/fw-vnc.zip
```

### Disable

Firewall rules are enabled right after the installation.
Rules can be selectively disabled by running:

```
esxcli network firewall ruleset set -e false -r VNC
```

### Uninstall

```
esxcli software vib remove -n fw-vnc
```
