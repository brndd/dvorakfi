# Finnish Dvorak keyboard layout

This is my homebrew Finnish Dvorak layout, created to include the Finnish characters *ä* and *ö* in convenient locations. It also has a bunch of other characters common in European and especially Nordic languages.

![preview](https://raw.githubusercontent.com/brndd/dvorakfi/master/preview.png)

# Installation

## Windows

1. [Download the installer here](https://github.com/brndd/dvorakfi/releases/download/1.0/dvorakfi_windows.zip)
2. Extract the archive
3. Run `setup.exe` to install the keymap
4. Activate the layout in the Control Panel's language menu. It's under the name "Finnish Unofficial Dvorak Keyboard Layout".

If you want to uninstall the layout entirely, you can do that from the Add and Remove Software section of the control panel.
If you want to edit the layout yourself, download Microsoft's [Keyboard Layout Creator](https://www.microsoft.com/en-us/download/details.aspx?id=22339) and open the `dvficstm.klc` file found in the archive.

## Linux (in short)

You can find more detailed instructions for Linux [here](linux/README.md).

1. [Download the keymap files here](https://github.com/brndd/dvorakfi/releases/download/1.0/dvorakfi_linux.zip)
2. Extract the archive
3. Copy dvficstm (no file extension) to the XKB keymap directory, which on at least Ubuntu and Fedora is `/usr/share/X11/xkb/symbols/`
4. Add the layout to `evdev.xml` (make a backup first), which similarly is found somewhere like `/usr/share/X11/xkb/rules/evdev.xml`. Open the file, find the line `</layoutList>`, and add this before that line, after the last `</layout>` tag:

```
xml
<layout>
  <configItem>
    <name>dvficstm</name>
    <shortDescription>fi</shortDescription>
    <description>Finnish Custom Dvorak keyboard</description>
    <languageList>
      <iso639Id>fin</iso639Id>
    </languageList>
  </configItem>
  <variantList/>
</layout>
```
5. You can also make the same change to the `base.xml` file in the same folder if you want to be extra sure (I really don't know what these files actually do).
5. If you want to use the keymap in the virtual console, copy `dvficstm.map.gz` to KBD's keymaps folder,
the location of which again depends on your distro but on Fedora is at `/usr/lib/kbd/keymaps/xkb/`.
You can then switch to the layout using the `loadkeys` command, or (probably again depending on your distro) set it as default using `localectl set-keymap dvficstm`

No guarantees on this persisting through updates. It's possible updates to xkb may overwrite your changes to `evdev.xml`. Extra info can be found on Google, which as a Linux user you're probably quite familiar with.

## OS X

I don't own a Mac, so I can't make a Mac version. If you port this over, do a pull request or email me if you want to include instructions here.
