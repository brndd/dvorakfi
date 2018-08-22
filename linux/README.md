# INSTALLATION INSTRUCTIONS AS OF 2017-08:

Linux installation is a little bit involved, and these instructions are subject
to stop working at any time, and may vary based on your distro. That's how Linux
is.

Put the `dvficstm` file in `/usr/share/X11/xkb/symbols/`, or your distro's
equivalent of this folder. This is the folder for X.org XKB keyboard layouts.
To make it appear in Gnome's (and probably every other DE's) keyboard layout
list, you'll have to create an entry for it in
`/usr/share/X11/xkb/rules/evdev.xml` (again, varies distro by distro).
Open `evdev.xml` (back it up first), search for `</layoutList>`,
and insert the following between the last `</layout>` tag and `</layoutList>`:

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

Save `evdev.xml` and reboot (or restart X.org). If things went right, you should
now see the layout in the keyboard layout options GUI. Note that there's also
a `base.xml` that seems to, at least on Fedora, contain the exact same list.
You may want to add the new keymap there as well. I have no idea what it does,
though.

Extended guide for this can be found here:
http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11


If you want to use this in the virtual console (you know, the scary thing that
opens when you press ctrl-alt-F2 or some other function key, these fuckers go
all the way up to F7), you'll have to convert the XKB file to a KBD file using
ckbcomp. I've already included a compiled KBD version of the keymap, though,
so you only have to do this if you change something yourself.

With the dvficstm file in `/X11/xkb/symbols/`, run:
```
ckbcomp dvficstm dvficstm | gzip > dvficstm.map.gz
```
This should produce a KBD keymap file in your current directory.

Move that to the appropriate KBD keymaps folder, which on Fedora is
`/usr/lib/kbd/keymaps/xkb/` but will vary by distro. Then you can load the
layout using `loadkeys dvficstm` or whatever.
On Fedora I used `localectl set-keymap dvficstm`, but that's probably some
systemd heresy.