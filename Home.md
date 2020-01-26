<p align="center">
  Welcome to the Cage wiki!
</p>

Cage is a kiosk compositor for Wayland. A kiosk is a window manager (in the X11 world) or compositor (in the Wayland world) that is designed for a user experience wherein user interaction and activities outside the scope of the running application are prevented. That is, a kiosk compositor displays a single maximized application at a time and prevents the user from interacting with anything but this application.

As such, user input such as moving, resizing, minimizing and unmaximizing windows is ignored. Cage supports dialogs, although they too cannot be resized nor moved. Instead, dialogs are centered on the screen. Note that multiple maximized windows are supported, but the user is not able to cycle between them. That is, if Cage is launched with a terminal emulator and an application is launched from this terminal emulator, that application is placed “on top” of the terminal emulator and takes all input until it is closed. When this application is closed, the terminal emulator becomes visible again. When the last application window is closed, Cage closes as well.

Cage supports multiple outputs. It supports hotplugging additional outputs and exits when its last output is removed. Cage defaults to the outputs' preferred modes and supports (static, i.e. specified on startup) output rotation. Cage does not support virtual workspaces. Input-wise, Cage supports pointer input, keyboard input and touch input. Copy and paste works as well, including primary selection and with full XWayland support.