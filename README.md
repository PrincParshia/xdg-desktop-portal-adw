# xdg-desktop-portal-adw

A backend implementation for [xdg-desktop-portal](http://github.com/flatpak/xdg-desktop-portal)
that is using GTK4 and Libadwaita.

## Installing

First, make sure to install the required dependencies:

```
cairo dconf fontconfig gcc-libs gdk-pixbuf2 glib2 glibc gnome-desktop-4 graphene gtk4 libadwaita libx11 nautilus xdg-desktop-portal xdg-desktop-portal-gtk
```

You may also install the make dependencies:

```
git meson glib2-devel
```

Then run the build and install command:

```
git clone https://github.com/PrincParshia/xdg-desktop-portal-adw.git
meson setup build --prefix=/usr
meson compile -C build
sudo meson install -C build
```
