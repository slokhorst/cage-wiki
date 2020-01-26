<h2 align="center">Welcome to the Cage wiki!</h1>

This wiki contains documentation to run Cage. For general Wayland-related questions, such as how to set a wallpaper or take screenshots, please see [Sway's wiki](https://github.com/swaywm/sway/wiki).

# What is Cage?

Cage is a kiosk compositor for Wayland. A kiosk is a window manager (in the X11 world) or compositor (in the Wayland world) that is designed for a user experience wherein user interaction and activities outside the scope of the running application are prevented. That is, a kiosk compositor displays a single maximized application at a time and prevents the user from interacting with anything but this application.

As such, user input such as moving, resizing, minimizing and unmaximizing windows is ignored. Cage supports dialogs, although they too cannot be resized nor moved. Instead, dialogs are centered on the screen. Note that multiple maximized windows are supported, but the user is not able to cycle between them. That is, if Cage is launched with a terminal emulator and an application is launched from this terminal emulator, that application is placed “on top” of the terminal emulator and takes all input until it is closed. When this application is closed, the terminal emulator becomes visible again. When the last application window is closed, Cage closes as well.

Cage supports multiple outputs. It supports hotplugging additional outputs and exits when its last output is removed. Cage defaults to the outputs' preferred modes and supports (static, i.e. specified on startup) output rotation. Cage does not support output layout configuration.

There is no support for virtual workspaces. Input-wise, Cage supports pointer input, keyboard input and touch input. Copy and paste works as well, including primary selection and with full XWayland support.

## List of supported protocols

The below is an alphabetically sorted list of supported protocols (without the out-of-the-box `wl_*` protocols). If you wish to see an additional protocol supported, first consider whether it fits Cage's use-case. It it does, [open an issue](https://github.com/Hjdskes/cage/issues/new) and explain your use-case. If you find a protocol to be implemented but not listed here, please edit this page or [open an issue](https://github.com/Hjdskes/cage/issues/new) to let us know.

* idle_inhibit_unstable_v1
* org_kde_kwin_idle
* server_decoration
* wlr_export_dmabuf_unstable_v1
* wlr_gamma_control_unstable_v1
* wlr_screencopy_unstable_v1
* xdg_decoration_unstable_v1
* xdg_output_unstable_v1
* xdg_shell