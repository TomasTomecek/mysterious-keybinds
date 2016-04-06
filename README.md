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


# kerberos

 * `export KRB5_TRACE=/dev/stdout` — prints debug logs to stdout


# docker

 * `docker inspect --format '{{ .NetworkSettings.IPAddress }}'` — get IP address of a container


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
