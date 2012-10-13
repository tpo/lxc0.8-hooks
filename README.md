lxc0.8-hooks
============

Hooks for lxc v0.8

[lxc](https://github.com/lxc/lxc) 0.8 does not allow you to hook into a
container and execute scripts at certain points in its lifecycle.

Ubuntu has backported this facility for its lxc 0.8, however Debian did
not.

lxc0.8-hooks is a simple wrapper around lxc-start and lxc-stop that
provides this facility.

lxc post v0.8 will have a hooks facility, so lxc0.8-hooks serves as an
interrim solution for those who need it with lxc v0.8.


Howto
=====

    cp bin/lxc-start bin/lxc-stop /usr/local/bin

Since /usr/local/bin comes first in your $PATH those scripts take
precedence over the executables in /usr/bin. The wrapper scripts will
execute your pre-start and post-stop scripts and then call
/usr/bin/lxc-start or /usr/bin/lxc-stop respectively.

    container="name of your container"
    mkdir "/var/lib/lxc/$container/hooks"

This is the place where you can create your <code>pre-start</code> and
<code>post-stop</code> scripts. They will be executed by lxc-start or
lxc-stop. The result should look like this:

    $ ls "/var/lib/lxc/$container/hooks"
    total 8
    -rwxr-xr-x 1 root root 172 Oct 12 22:21 post-stop
    -rwxr-xr-x 1 root root 128 Oct 12 21:46 pre-start


License
=======

These scripts are in the public domain.

Tomáš Pospíšek <tpo_deb@sourcepole.ch>
