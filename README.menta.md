# pkg-mate-redshift (Menta Linux)

Debian packaging for [KeremSoke/mate-redshift](https://github.com/KeremSoke/mate-redshift),
the Night Light settings dialog for MATE. There is no Debian/Salsa package, so `debian/` is
written from scratch.

Built from an upstream **git commit**, not a release (none exists for the latest commit).
Version: `<meson version>+git<date>.<short hash>-1menta1`, e.g.
`0.1.0+git20261022.c2f3fba-1menta1`. CI clones the repo, checks out the hash from the
version string and makes the orig tarball with `git archive`. To package a newer commit,
bump the date and hash in `debian/changelog` (`dch`).

- Runtime dependency: `rojo` (menta `pkg-rojo`, `/usr/bin/rojo`). The dialog talks to it over
  D-Bus (`org.mate.rojo`) and uses its GSettings schema. Building does not need rojo.
- Wayland: nothing to enable here. mate-redshift is a plain GTK dialog; Wayland works through rojo.
- No applet, so nothing to build in-process.
- Patch: `0001-install-desktop-file.patch` (upstream does not install the .desktop file).
