# Note: now running on gnome-shell 3.3+
It's still in development, but much easier since it requires no modifications to `mutter`. After cloning the `master` branch, you can run it with:

	0launch --not-before=0.4-pre shellshape-local.xml --replace

# shellshape
A tiling window manager extension for gnome-shell. Many tiling window managers are an all-or-nothing affair, shellshape allows you to tile your windows when it makes sense, and still provides powerful direct manipulation when you need it. You don't have to give up any of the gnome features you like, so it makes for a very smooth learning curve.

This software is in-development. I use it daily, but it might break stuff. Use at your own risk.

I must thank [bluetile][bluetile], for it was the inspiration for this extension and many features are lifted directly from it (although not code, JS and haskell are vastly different beasts).

## Running it on gnome-shell 3.2*
Please see instructions on <http://gfxmonk.net/shellshape/>

To run your own checkout, you should be able to clone this repo and run `0launch shellshape-local.xml`.

## running on arch linux

You may want to try [this user-maintained package](https://aur.archlinux.org/packages.php?ID=50257) if the normal method doesn't work for you, but I have no idea what it will do to your system.

## "It doesn't work"

If you don't know why, here's some things to check:

	- Check the extension is enabled (you can see this in the "Shell Extensions" section of `gnome-tweak-tool`)
	- See if there are any errors in looking glass that mention shellshape (press alt-F2, type "`lg`" and then click the "Errors" tab)
	- Check the console output (if running in a console) for any messages that mention shellshape
	- Check /tmp/shellshape.log after launching with $SHELLSHAPE_DEBUG=all

To report a bug or crash, please see the [github issues page](https://github.com/gfxmonk/shellshape/issues).

## Replace gnome-shell

If you symlink the provided `gnome-shell.desktop` file to `~/.local/share/applications/`, gnome-session will use that to launch gnome-shell instead of the system's gnome-shell. Uninstalling is as simple as removing that file.

## Friends
This extension is best used with the natural window placement extension.

Other extensions I use and recommend:

 - alternate status menu (the fact that this is not default bewilders me)
 - workspace switcher

All of these should be available from your package manager, or [the gnome shell extensions page](https://live.gnome.org/GnomeShell/Extensions)

## Hacking
The core layout stuff is in `tiling.coffee`. This should run in both the shell and in the web browser (see `interactive/index.html`; useful for testing layout changes). The mutter / gnome-shell integration is provided by the other .js files in the root directory (except for `tiling.js`, it is generated from `tiling.coffee`).

## Debugging
If you export `SHELLSHAPE_DEBUG=all`, you will get a debug log written to `/tmp/shellshape.log`. You can set values other than `all` if you want to debug on specific topics (available topics include `extension`, `indicator`, `tiling`, `workspace` and `window`) - they should be set as a comma-delimited string, e.g `SHELLSHAPE_DEBUG=workspace,tiling`.

## Licence
GPLv3

[bluetile]: http://bluetile.org/
