# Mysterious Keybinds, Shortcuts, Commands, Options

## git

 * cherry-pick a selected set of commits:
   * g cherry-pick <bottom-commit>^..<top-commit>
 * cancelling a commit: type `:cq` in vim
 * listing refs in a remote: `git ls-remote`
 * ignore SSL errors: `export GIT_SSL_NO_VERIFY=true`
 * adding existing dir as a submodule:
   * `git submodule add <remote_url> <path>`
 * initialize existing submodules:
   * `git init` & `git update`

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
 * `:e` — if swapfile is detected, this will reopen the file and allow deletion
  * https://stackoverflow.com/a/220543/909579
 * `K` — man page for that word


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
  * `strace -e '/.*open.*' — filter by regex
  * `-c -w` — wall clock time spent on syscalls

 * `grep`
  * `-e` — boolean OR, e.g. `grep -e INFO -e DEBUG file.log`
  * OR `egrep (...|...|...)

 * `xset`
  * `-q` — test connection to X server

 * `useradd [-u 1000] lojza`
 * `usermod -a -G mock`


# pentadactyl

 * `gi` — google docs input


# git

## github

 * fetch PRs locally:

  ```
  fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
  ```


# Travis CI
 * CLI: `docker run -ti -v $PWD:/project --rm --entrypoint=sh skandyla/travis-cli`
   * `travis login --github-token`
   * `travis setup releases`


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


# OpenShift

 * `oc explain pod.spec.containers` show all the options

 * log in to registry
   * `oc login "<OPENSHIFT_INSTANCE>"`
   * `docker login -u ttomecek -p $(oc whoami -t) "<REGISTRY>"`


# SELinux

 * `semanage port -l` list policies for ports


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
 * `pkill -o mosh-server` — kill oldest mosh-server process


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

 * install using pip from a git repo:
   ```
   $ pip3 install git+https://github.com/TomasTomecek/sen.git@1bfab11eb1ad5183fc0722fb62254adaae5bea14
   ```

 * versioning syntax: `[N!]N(.N)*[{a|b|rc}N][.postN][.devN]`

 * pytest

   * tmpdir fixture
     ```
     def test_create_file(tmpdir):
     p = tmpdir.mkdir("sub").join("hello.txt")
     p.write("content")
     assert p.read() == "content"
     assert len(tmpdir.listdir()) == 1
     ```
 * decorator
   ```
   def my_decorator(func):
       def wrapper():
           func()
   return wrapper
   ```
 * flexmock
   * mock a function: `flexmock(module, function=lambda x, y: data)`

 * python source file encoding: `# -*- coding: utf-8 -*-`


# CGroups

 * remove by doing `rmdir` of leafs — do not remove files!


## Planning

[Source](https://www.youtube.com/watch?v=kOSFxKaqOm4&index=33&list=WL&t=1s)

 * Purpose (Why?)
 * Vision (What?)
 * Ideas (Brainstorming)
 * Structure (Details)
 * Next action (Timeline)


## Vagrant

Usable Vagrantfile to use with Fedora box:
```
Vagrant.configure(2) do |config|
    config.vm.provider "libvirt" do |libvirt, override|
        libvirt.memory = 2048
        libvirt.cpus = 2
    end
    config.vm.box = "fedora/28-cloud-base"
    config.vm.provision :ansible do |ansible|
        ansible.limit = "all"
        ansible.playbook = "provision.yml"
        ansible.raw_arguments = ["-e", "ansible_python_interpreter=/usr/bin/python3"]
    end
end
```


## Ansible

Sensible ansible.cfg
```
[defaults]
retry_files_enabled = false
enable_task_debugger = True
stdout_callback = dense,debug,unixy,yaml,minimal
# strategy = debug
```

Nicer output:
```
ANSIBLE_STDOUT_CALLBACK=debug
```
