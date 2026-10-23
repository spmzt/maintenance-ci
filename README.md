# FreeBSD Maintenance CI

There are three pipelines here.

## pkgbase

Pulls `/usr/src` (not when the tree has local changes: it is built as it
is), rebuilds the pkgbase repository with `poudriere jail -u`, snapshots the
jails dataset, upgrades the basejail from the new packages, and destroys its
own snapshots past the newest `keep_snapshots` (3).

## Jail

Builds a minimal FreeBSD container image from pkgbase with buildah and pushes
it to the registry; the dated tag is then dropped locally and dangling images
pruned.

## Ports

Triggers poudriere bulk, then cleans packages no longer listed, logs older
than 30 days and unused distfiles.
