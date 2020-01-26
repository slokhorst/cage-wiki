# Troubleshooting

When you have an issue with Cage, please update both Cage and wlroots and then try again. It may be that a newer version has already fixed your problem. If not, look through [known issues in Cage](https://github.com/Hjdskes/cage/issues) and [known issues in wlroots](https://github.com/swaywm/wlroots/issues). Read this Wiki and ensure the solution to your problem isn't already described somewhere.

For any issue that doesn't directly relate to Cage (i.e., is an application using Wayland or XWayland, or application settings), please don't open an issue. [Sway's wiki](https://github.com/swaywm/sway/wiki#faq) contains some frequently asked questions, but please don't open an issue on Sway's bug tracker either.

## How do I report issues?

When opening bug reports, please provide three things: your Cage version (`cage -v`), your wlroots version and Cage's log (`cage 2> cage.log`).

The latter command will redirect Cage's output to the file `cage.log`. While running Cage like this, try to briefly reproduce the problem and then close Cage. It's important to make this interaction as short as can be to show the problem. Upload this file to a pastebin (e.g. [gist.github.com](gist.github.com)) and attach the link to your GitHub issue. List the steps you took in your GitHub issue as well.

If the problem isn't immediately obvious, you will likely be required to debug it yourself - we are volunteers and only have so much free time.

## Cage is unable to drop root

See [here](https://github.com/Hjdskes/cage/wiki/Running-Cage-without-systemd).