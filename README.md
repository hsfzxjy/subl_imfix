# subl_imfix
Fix up input methods bug in sublime text.

## NOTICE
Every time you change a machine, you might recompile it.

## Configuration
Install dependecies:

```sh
sudo apt-get install build-essential
sudo apt-get install libgtk2.0-dev
```

Compile:

```sh
gcc -shared -o libsublime-imfix.so sublime-imfix.c `pkg-config --libs --cflags gtk+-2.0` -fPIC
```

Move `libsublime-imfix.so` into `/opt/sublime_text/`.

Modify `/usr/bin/subl`:

```sh
#!/bin/sh

export LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so
exec /opt/sublime_text/sublime_text "$@"
```