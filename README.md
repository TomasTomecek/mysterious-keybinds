# Mysterious Keybinds, Shortcuts, Commands, Options

## vim

 * `C - {H, J, K, L}` — movement across splits
 * `C-w`
  * `[N] - +` — height adjustment
  * `[N] < >` — width adjustment
  * `=` — equality
  * `_ |` — maximal adjustment
  * `r` — swap positions
  * `T` — break window into a new pane
 * `"*` — clipboard (e.g. `"*p`)
 * `C-r x` — paste registry `x` (INS mode)
 * `:e!` — reload file
 * `:jumps` — history
 * `:ls` — list open files
 * `:b` — navigate to buffer


### fugitive

 * `:G{edit,vsp,sp}` ref:file


### jedi

 * `<leader>g` — go to definition
 * `<leader>d` — go to original definition


## vimdiff

 * `:e`
 * `:set [no]scrollbind`
 * `z[rR]` — folding reduce
 * `z[mM]` — folding more
 * `do` — diff get
 * `dp` — diff put
 * `:diffg {RE,BA,LO}` — diff get
 * `:diff update`


## commands

 * `less`
  * `-S` — wrap lines

 * `strace`
  * `-s1024 -f` — string buffer length
  * `strace -e trace=open,read,write` — filter syscalls

 * `grep`
  * `-e` — boolean OR, e.g. `grep -e INFO -e DEBUG file.log`
  * OR `egrep (...|...|...)

 * `xset`
  * `-q` — test connection to X server

# pentadactyl

 * `gi` — google docs input


# git

## github

 * fetch PRs locally:

  ```
  fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
  ```


# mc

 * `+` — regex to mark entries
 * `ctrl+t` — mark a single entry
 * `F9 r Shell link` — user@host — filesystem over SSH in MC
 * `alt+O` open select dir on other panel
 * `alt+I` dupe panel


# kerberos

 * `export KRB5_TRACE=/dev/stdout` — prints debug logs to stdout


# docker

 * `docker inspect --format '{{ .NetworkSettings.IPAddress }}'` — get IP address of a container
 * access registry from CLI:
   ```
   IMAGE=library/redis
   TAG=latest
   TOKEN=$(curl -s "https://auth.docker.io/token?scope=repository:$IMAGE:pull&service=registry.docker.io" | jq -r .token)
   CONFIG_DIGEST=$(curl -s -H"Accept: application/vnd.docker.distribution.manifest.v2+json" -H"Authorization: Bearer $TOKEN" "https://registry-1.docker.io/v2/$IMAGE/manifests/$TAG" | jq -r .config.digest)
   ENTRYPOINT=$(curl -sL -H"Authorization: Bearer $TOKEN" "https://registry-1.docker.io/v2/$IMAGE/blobs/$CONFIG_DIGEST" | jq -r .container_config.Entrypoint)
   echo $ENTRYPOINT
   ```
   [source](https://github.com/docker/distribution/issues/1252#issuecomment-274944254)


# sysrq

https://www.kernel.org/doc/Documentation/sysrq.txt

```
'f' - Will call the oom killer to kill a memory hog process, but do not
      panic if nothing can be killed.

'r' - Turns off keyboard raw mode and sets it to XLATE.

On x86
    - You press the key combo 'ALT-SysRq-<command key>'. Note - Some
      keyboards may not have a key labeled 'SysRq'. The 'SysRq' key is
      also known as the 'Print Screen' key. Also some keyboards cannot
      handle so many keys being pressed at the same time, so you might
      have better luck with "press Alt", "press SysRq", "release SysRq",
      "press <command key>", release everything.
```

After setting mode to XLATE, we need to set it back to RAW: `kbd_mode -s`:

```
 -s: scancode mode (RAW)
```


# npm

 * `npm v` — info about a npm module
 * `npm v <pkg> versions` — all versions of a module


# EPEL

 * `rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm` — one command to install EPEL 7


# ruby

 * installing extensions with native code:
  * `gem install --verbose --debug --backtrace`
  * open `mkmf.log`


# Networking

 * list routing table: `ip r[oute]`
 * get interface which will route the traffic `ip r get <IP>`


# dbus

 * test dbus connection & list available methods:

```
$ dbus-send --system          \
  --dest=org.freedesktop.DBus \
  --type=method_call          \
  --print-reply               \
  /org/freedesktop/DBus       \
  org.freedesktop.DBus.ListNames
```

```
$ dbus-send --session           \
  --dest=org.freedesktop.DBus \
  --type=method_call          \
  --print-reply               \
  /org/freedesktop/DBus       \
  org.freedesktop.DBus.ListNames
```


# shell

 * `-eq` for integers
 * `==` for strings
 * `[[ x || y ]]` — `x` or `y`


# python

 * context manager
    ```python
    class A():
        def __init__(self):
            pass

        def __enter__(self):
            return None

        def __exit__(self, *args):
            pass

    with A() as a:
        pass
    ```
