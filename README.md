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

