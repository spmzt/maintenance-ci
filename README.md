# FreeBSD Maintenance CI

There are three pipelines here.

## pkgbase

Pulls `/usr/src`, rebuilds the pkgbase repository with `poudriere jail -u`,
snapshots the jails dataset and upgrades the basejail from the new packages.

## Jail

Builds a minimal FreeBSD container image from pkgbase with buildah and pushes
it to the registry.

## Ports

Triggers poudriere bulk
