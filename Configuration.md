Before reading this and opening issues, please keep in mind that Cage is *not* a usual compositor. It fulfills a specific niche and will not fit into a regular desktop-style workflow.

# Configuration

There is no configuration for Cage, other than command line arguments on startup (see `-h`) and a limited number of environment variables (see below). To start Cage, simply call its binary with the path to the application you want to launch within the session. For example, use `cage /usr/bin/epiphany` to launch Cage with the Epiphany web browser. To pass arguments to the application, separate it from Cage's arguments with two dashes: `cage -- /usr/bin/epiphany -i`.

## Display configuration

Cage manages displays for you, and the configuration can be updated via tools such as wlr-randr or kanshi (via the wlr-output-management Wayland protocol). Cage spans application windows across the bounding box of the output layout. If the output layout does not fill this bounding box, then parts of the application will be drawn outside of your displays and therefore be hidden:

```
+---------------------------------+---------------------------------------+
|                                 |                                       |
|                                 |                                       |
|                                 |                                       |
|                                 |                                       |
|            Secondary            |                                       |
|             monitor             |                                       |
|            (smaller)            |                                       |
|                                 |                                       |
|                                 |                                       |
|                                 |                                       |
+---------------------------------+        Primary monitor (larger)       |
|                                 |                                       |
|                                 |                                       |
|  Invisible part of the window   |                                       |
|                                 |                                       |
|                                 |                                       |
+---------------------------------+---------------------------------------+
```

## Environment variables

Cage sets the following environment variables:

* `DISPLAY`: if compiled with Xwayland support, this will be set to the name of
  the X display used for Xwayland.
* `WAYLAND_DISPLAY`: specifies the name of the Wayland display that Cage is
  running on.

The following environment variables can be used to configure behavior of
libraries that Cage uses.  Effectively, these environment variables configure
the Cage session.

### XKB environment variables

```
XKB_DEFAULT_RULES
XKB_DEFAULT_MODEL
XKB_DEFAULT_LAYOUT
XKB_DEFAULT_VARIANT
XKB_DEFAULT_OPTIONS
```

These environment variables configure the XKB keyboard settings. See
xkeyboard-config(7).

### Wlroots environment variables

* `DISPLAY`: if set probe X11 backend.
* `WAYLAND_DISPLAY`, `_WAYLAND_DISPLAY`, `WAYLAND_SOCKET`: if set probe Wayland
  backend.
* `XCURSOR_PATH`: directory where xcursors are located.

For a complete list of wlroots environment variables, see
https://github.com/swaywm/wlroots/blob/master/docs/env_vars.md.