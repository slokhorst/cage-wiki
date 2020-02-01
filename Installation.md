Cage may be packaged for your distribution, see [repology](https://repology.org/project/cage/packages). This should be your preferred way to install Cage, unless that version is old or you need a newer feature not yet packaged.

To build Cage from source, you can grab [a release](https://github.com/Hjdskes/cage/releases/). The release specifies which version of wlroots it should be built against. Releases are signed with
[6EBC43B1](http://keys.gnupg.net/pks/lookup?op=vindex&fingerprint=on&search=0x37C445296EBC43B1). Alternatively, you can grab the latest master branch from [GitHub](https://github.com/Hjdskes/cage). Note that Cage is developed against the latest tag of wlroots, in order to not constantly chase breaking changes as soon as they occur.

Cage is built with the [meson](https://mesonbuild.com/) build system. It requires wayland, wlroots and xkbcommon to be installed. Simply execute the following steps to build Cage:

```
$ meson build
$ ninja -C build
```

By default, this builds a debug build. To build a release build, use `meson build --buildtype=release`.

Cage comes with compile-time support for XWayland. To enable this, first make sure that your version of wlroots is compiled with this option. Then, add `-Dxwayland=true` to the `meson` command above. Note that you'll need to have the XWayland binary installed on your system for this to work.

You can run Cage by running `./build/cage APPLICATION`. If you run it from within an existing X11 or Wayland session, it will open in a virtual output as a window in your existing session. If you run it at a TTY, it'll run with the KMS+DRM backend. In debug mode (default build type with Meson), press <kbd>Alt</kbd>+<kbd>Esc</kbd> to quit. For more configuration options, see [Configuration](https://github.com/Hjdskes/cage/wiki/Configuration).
