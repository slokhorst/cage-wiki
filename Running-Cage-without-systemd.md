Cage makes use of systemd's logind to handle sessions and to allow Cage to run without elevated privileges. This is the recommended way to use Cage.

However, we understand that not everybody is using a systemd based distribution or even Linux, so there are alternative ways to handle this. Please do keep in mind that this way of using Cage sees next to no developer attention and that you're therefore more likely to run into issues. When opening any issues, please mention if you're not using logind.

# elogind

[elogind](https://github.com/elogind/elogind) is a project to take systemd's logind and separate it into an external program that can be run without the rest of systemd. This is the recommended way for users not using systemd.

To use elogind, wlroots should be compiled with `-Dlogind=enabled -Dlogind-provider=elogind`, or it will try to use `libsystemd` instead.

Make sure elogind is running and configured correctly before starting Cage. Refer to your distribution's documentation for details.

# Direct via setuid

_Note: Attempting to run Cage this way without this being configured correctly will probably leave your system in an unresponsive state, requiring a reboot_

To have Cage run as root in order to gain access to the resources it needs, you must set the setuid bit on the Cage executable with `chmod +s /usr/bin/cage`.

Cage will fork into a minimal slave process to keep these privileges, while dropping its own. As with any program, using setuid has serious security implications.
