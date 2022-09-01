# gtk-filechooser-patches
patches for using GtkFileChooserNative via the GtkFileChooserDialog interface.

I haven't done much testing so undefined behavior is possible. I also do not recommend installing a patched library as a system one.
it is better to use it via LD_PRELOAD for programs that do not support the use of portals out of the box.

to install, download the GTK3 sources (https://gitlab.gnome.org/GNOME/gtk/-/tree/gtk-3-24)
download the files from this repository to the gtk source root folder and run the following commands:
```
patch -u gtk/gtkdialog.c -i gtkdialog.c.patch
patch -u gtk/gtkdialog.h -i gtkdialog.h.patch
patch -u gtk/gtkfilechooserdialog.c -i gtkfilechooserdialog.c.patch
patch -u gtk/gtkfilechoosernativeprivate.h -i gtkfilechoosernativeprivate.h.patch
patch -u gtk/gtkfilechoosernative.c -i gtkfilechoosernative.c.patch
```

gtk build:
```
meson build
ninja -C build
```

the environment variable must also be set: GTK_USE_PORTAL=1
