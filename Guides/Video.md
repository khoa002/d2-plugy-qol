# D2QOL | Video

Custom video libraries are necessary to make Diablo II run properly on modern machines.

Historically, the D2 community has used the ``Glide`` library, but more recently the community has been introduced to the ``DDraw`` library which allows for better framerates and performance.  I recommend installing the ``DDraw`` library which has drastically improved game performance on my machine.

The D2QOL modpack comes with both libraries preinstalled, so you won't need to redownload them.  If using ``DDraw`` you still need to make the necessary registry changes and if using ``Glide`` you still need to make the necessary settings changes as instructed below.

## DDraw

- Download the [v1.3.5](https://github.com/CnCNet/cnc-ddraw/releases) files.
- Download my updated [config](https://github.com/whipowill/d2-plugy-qol/blob/master/Diablo%20II/Mod%20PlugY/ddraw.ini) file customized for D2.
- Copy the files into your D2 directory.
- Open ``regedit`` on your Windows machine:
	- Navigate to ``HKEY_CURRENT_USER\Software\Blizzard Entertainment\Diablo II\VideoConfig``.
	- Change the ``Render`` value to zero.
- Modify your PlugY shortcut target to include ``-direct -txt`` (do not use ``-w -3dfx -nofixaspect``).
- When using PlugY you need to make sure the files to the right locations:
	- ``C:/Games/Diablo II/ddraw.dll``
	- ``C:/Games/Diablo II/Mod PlugY/ddraw.ini``
	- ``C:/Games/Diablo II/Shaders/``

The shaders and upscaling of graphics only works on Windows and Linux.  It seems like there is a problem with OpenGL on Mac that prevents the shaders from working, although DDraw will work just fine otherwise.

### Wine

If you're using Wine you'll have to use the command line.

- Edit the registry:
```bash
$ WINEPREFIX=~/.wine_d2plugy regedit
> Navigate to HKEY_CURRENT_USER\Software\Blizzard Entertainment\Diablo II\VideoConfig.
> Change the Render value to zero.
```
- Edit the Wine config:
```bash
$ WINEPREFIX=~/.wine_d2plugy winecfg
> On the Applications tab, run as Windows XP.
> On the Libraries tab, add override for "ddraw".
```
- Modify your Terminal alias:
```bash
$ vim .bashrc
> alias d2plugy="cd ~/.wine_d2plugy/drive_c/games/diablo\ ii/mod\ plugy && WINEPREFIX=~/.wine_d2plugy wine plugy.exe -direct -txt"
```
- Reload your Terminal and play the game:
```bash
$ d2plugy
```

## Glide

- Download the [v1.4e](http://www.svenswrapper.de/english/files.html) files.
- Copy the files into your D2 directory.
- Run the ``glide-init.exe`` file and modify the settings:
	- Switch to ``English``.
	- On the ``Settings`` tab:
		- Turn on ``window-mode``.
		- Turn on ``keep aspect ratio``.
		- Turn on ``centerered``.
	- On the ``Renderer`` tab:
		- Turn on ``32 bit rendering``.
		- Turn on ``texture for videos``.
		- Turn on ``bilinear filtering``.
		- Turn on ``no gamma``.
	- On the ``Extensions`` tab:
		- Turn on ``MGL_EXT_swap_control``.
- Modify your PlugY shortcut target to include ``-w -3dfx -nofixaspect -direct -txt``.

### Wine

If you're using Wine you'll have to use the command line.

- Run the ``glide-init.exe`` executable:
```bash
$ cd ~/.wine_d2plugy/drive_c/games/diablo\ ii
$ WINEPREFIX=~/.wine_d2plugy wine glide-init.exe
```
- Modify your Terminal alias:
```bash
$ vim .bashrc
> alias d2plugy="cd ~/.wine_d2plugy/drive_c/games/diablo\ ii/mod\ plugy && WINEPREFIX=~/.wine_d2plugy wine plugy.exe -w -3dfx -nofixaspect -direct -txt"
```
- Reload your Terminal and play the game:
```bash
$ d2plugy
```