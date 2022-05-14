# Finnish Dvorak keyboard layout

This is my homebrew Finnish Dvorak layout, created to include the Finnish characters *ä* and *ö* in convenient locations. It also has a bunch of other characters common in European and especially Nordic languages.

![preview](https://raw.githubusercontent.com/brndd/dvorakfi/master/preview.png)

# Installation

## Windows

1. [Download the installer here](https://github.com/brndd/dvorakfi/releases)
2. Extract the archive
3. Run `setup.exe` to install the keymap
4. Activate the layout in the Control Panel's language menu. It's under the name "Finnish Unofficial Dvorak Keyboard Layout".

If you want to uninstall the layout entirely, you can do that from the Add and Remove Software section of the control panel.
If you want to edit the layout yourself, download Microsoft's [Keyboard Layout Creator](https://www.microsoft.com/en-us/download/details.aspx?id=22339) and open the `dvficstm.klc` file found in the archive.

## Linux (in short)

**Update: this is included in the xkeyboard-config package (and has been for many years now, actually). It is in the "extras" section; some systems, e.g. KDE, show it by default among all the other Finnish keyboard layouts. On GNOME, you need to use gnome-tweaks to enable the "Show Extended Input Sources" option (apparently—I have not tested this) as per [this SuperUser answer](https://superuser.com/a/1719180.**

You can find more detailed instructions for Linux [here](linux/README.md). Also, this should be available in xkeyboard's extras package now; you should be able to find it among the other Finnish keymaps under the name "Finnish Dvorak" (symbols name: fidvorak).

1. [Download the keymap files here](https://github.com/brndd/dvorakfi/releases)
2. Extract the archive
3. Copy dvficstm (no file extension) to the XKB keymap directory, which on at least Ubuntu and Fedora is `/usr/share/X11/xkb/symbols/`
4. Add the layout to `evdev.xml` (make a backup first), which similarly is found somewhere like `/usr/share/X11/xkb/rules/evdev.xml`. Open the file, find the line `</layoutList>`, and add this before that line, after the last `</layout>` tag:

```xml
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

# Dramatic backstory

I've used a Dvorak keyboard layout over the standard QWERTY keyboard for many years now.
I originally swapped over almost extemporaneously sometime around 2010-2011 after an IRC acquintance mentioned he was using Dvorak.
I liked the idea of a more ergonomic home row, and Dvorak is worth way more hipster cred than the normie tier QWERTY.

The problem was, there is no "official" Finnish Dvorak layout. There were a couple of existing layouts online, although only [ArkkuDvorak](http://arkku.com/dvorak/) seems to be around now.
ArkkuDvorak is a bit... well, *very* silly in that it puts the Finnish Ä and Ö characters on the same key — the <>| -key
that is present on the Finnish (and a handful of other European) keyboards, but missing on the US layout.
What's more, the way it worked was that pressing the key normally produced a lower-case Ä, while pressing it with Shift produces a lower-case Ö.
The upper-case versions of these letters were behind an AltGr modifier. I didn't like this at all, so I decided
to make my own flavour of Dvorak.

I based my layout on an alternate Finnish Dvorak layout I found online, which seems to have vanished from the intertubes since then.
The layout was called **Suomalainen monikielinen Dvorak** (*Finnish multilingual Dvorak*), but I can't remember the name of the author. If you're reading, thanks a bunch!

If I remember correctly, on that layout Ä and Ö were behind an AltGr modifier on A and O, respectively. I didn't like that either; they're common letters in the Finnish language, so I wanted them to have keys of their own.
I solved this by binding Ä to the extra <>| key which was unused in regular Dvorak, and Ö to the key next to it, the Z key on QWERTY.
On Dvorak, this key is used for colon : and semicolon ;, so to make room I moved these behind a shift modifier on comma and period, much like on QWERTY.
This displaced the < and > symbols, so I moved those behind an AltGr modifier instead. This way I could fit both Ä and Ö on their own keys without losing any functionality.
They ended up in a pretty good spot, too: in Dvorak all vowels are pressed with the fingers of the left hand.
The Swedish character Å, also occasionally used in Finnish, was left behind an AltGr-modifier on O, as I write very little Swedish.
It's still a pretty alright place for it anyway.

Over the years I've modified the layout as the need arises. Mostly I've added commonly used symbols that were absent (and are also absent on the QWERTY layout!).
For instance the degree sign ° is behind AltGr-0, en and em dash are behind an AltGr modifier on the regular dash; en dash with just AltGr and em dash with AltGr-Shift.
The mu symbol µ is under AltGr-M. The macron, ¯, commonly used in Japanese romanization to mark a long vowel, is under Shift-AltGr-Ö (that's QWERTY layout Z),
while the diaeresis ¨ is under the same key but without shift. And a bunch of other more or less useful special characters.

The layout isn't designed to be complete for any particular foreign language, however. It should have all the necessary symbols for all Nordic languages, though.
If you can't find the glyphs you need, go ahead and add them yourself! Editing the keymap is pretty straightforward.
