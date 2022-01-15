# Troubleshooting

When you have an issue with Cage, please update both Cage and wlroots and then try again. It may be that a newer version has already fixed your problem. If not, look through [known issues in Cage](https://github.com/Hjdskes/cage/issues) and [known issues in wlroots](https://github.com/swaywm/wlroots/issues). Read this Wiki and ensure the solution to your problem isn't already described somewhere. If this Wiki doesn't describe your problem, [Sway's Wiki](https://github.com/swaywm/sway/wiki#troubleshooting) also lists many common problems. 

For any issue that doesn't directly relate to Cage (i.e., is an application using Wayland or XWayland, or application settings), please don't open an issue. Please don't open an issue on Sway's bug tracker either.

## How do I report issues?

When opening bug reports, please provide three things: your Cage version (`cage -v`), your wlroots version and Cage's log (`cage 2> cage.log`).

The latter command will redirect Cage's output to the file `cage.log`. While running Cage like this, try to briefly reproduce the problem and then close Cage. It's important to make this interaction as short as can be to show the problem. Upload this file to a pastebin (e.g. [gist.github.com](gist.github.com)) and attach the link to your GitHub issue. List the steps you took in your GitHub issue as well.

If the problem isn't immediately obvious, you will likely be required to debug it yourself - we are volunteers and only have so much free time.

## Cage is unable to drop root

See [here](https://github.com/Hjdskes/cage/wiki/Running-Cage-without-systemd).

## Touch input isn't transformed correctly to my transformed touch output

For Cage to transform the touch input on your rotated device, the input device needs to be mapped to the output device. If you have this problem, your input device isn't reporting the output device it should be mapped to.

This can be resolved by adding a [udev](http://man7.org/linux/man-pages/man7/udev.7.html) rule that adds this device property to your input device. For example, to fix this issue for the FT5406 Raspberry Pi touchscreen, we'd add this udev rule to `/etc/udev/rules.d/95-rpi-ft5406.rules`:

```
# This udev rule maps the touch input device to the output device, such that transformations are 
# applied correctly in wlroots-based Wayland compositors.
#
# $ udevadm info --attribute-walk --path=$(udevadm info --query=path --name=/dev/input/event0)
KERNEL=="event[0-9]", SUBSYSTEM=="input", ATTRS{name}=="FT5406 memory based driver", ENV{WL_OUTPUT}="DSI-1"
```

This requires you to know the path in `/dev` of your input device and the name of your output device. The latter is printed by Cage (look for a log line "Scanning DRM connectors"), the former requires a bit of experimenting 
with devices listed under `/dev/input/`. In the case of the FT5406 touchscreen, there are little properties to match on besides the name. If your device has more properties, you can match on those as well.

## Cage does not start without any input devices

The default behavior of wlroots' libinput backend is to fail when there are no input devices. To disable this behavior, set the `WLR_LIBINPUT_NO_DEVICES` to `1` before launching Cage: `WLR_LIBINPUT_NO_DEVICES=1 cage /path/to/application`. You can also add this to the systemd service file:

```ini
[Service]
Environment=WLR_LIBINPUT_NO_DEVICES=1
```