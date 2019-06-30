# pinpoint-flatpak
[Flatpak](https://www.flatpak.org) recipe for the [pinpoint](https://wiki.gnome.org/Apps/Pinpoint) presentation application. This is now available from [Flathub](https://github.com/flathub/org.gnome.Pinpoint). You should get it there.

Installing:
-----------
Get it from [Flathub](https://github.com/flathub/org.gnome.Pinpoint)


Instructions:
-------------

(1) Install the flatpak repository for Flathub:
```
flatpak remote-add --from flathub https://flathub.org/repo/flathub.flatpakrepo

```
(2) Install the required runtimes
```
  flatpak install gnome org.gnome.Sdk//3.32
  flatpak install gnome org.gnome.Platform//3.32
```
(3) Build the app from this directory:
```
flatpak-builder --force-clean --ccache --require-changes --repo=repo app org.gnome.Pinpoint.json
```
(4) Add a remote to your local repo and install it:
```
flatpak --user remote-add --no-gpg-verify pinpoint-repo /path/to/your/flatpak/repo
flatpak --user install pinpoint-repo org.gnome.Pinpoint
```
(5) Run the Pinpoint app:
```
flatpak run org.gnome.Pinpoint
```
You'll need to use command line options to use the app: 
```
flatpak run org.gnome.Pinpoint -h
```
Gives you the list. You can access files within your home folder by default.

Note that if you do further changes in the `appdir` (e.g. to the metadata) you'll need to update before running it again:
```
flatpak --user update org.gnome.Pinpoint
```

Last, you can bundle it to a file with the `build-bundle` subcommand:
```
flatpak build-bundle /path/to/your/flatpak/repo org.gnome.Pinpoint.flatpak org.gnome.Pinpoint
```
