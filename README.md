# `check-pkgs`: Taming the package zoo

`check-pkgs` helps you manage [APT](https://wiki.debian.org/Apt), so you only
the packages you actually want are installed.

It does this by requiring that each package is either

 - A dependency of another (wanted) package.
 - Or explicitly marked as wanted by the user.

## Usage

RTFM:

```
$ check-pkgs --help
usage: check-pkgs [--list orphaned|dowant|ignore|remind|delete]

Pro tip:
  $ echo 'DPkg::Post-Invoke {"PATH/TO/THIS/SCRIPT";};' > /etc/apt/apt.conf.d/99check-pkgs
```

To check for orphaned packages simply run `check-pkgs` with no arguments.

### Run automatically

To automatically run `check-pkgs` each time you install or remove something with
APT, put this line in `/etc/apt/apt.conf.d/99check-pkgs`:

```
DPkg::Post-Invoke {"PATH/TO/THIS/SCRIPT";};
```

## Lists

Four lists are saved in `~/.pkgs`:

 - `dowant.pkgs`: Packages that must be installed.

 - `ignore.pkgs`: Packages that *can* be installed but doesn't need to be
   (useful if you e.g. use Gimp sometimes but don't want to have it installed
   always).

 - `delete.pkgs`: Packages that must not be installed.

 - `remind.pkgs`: Packages that the user has not decided whether should be
   installed or not.  Packages on this list are automatically deleted after
   five days.

## Installing

Place `check-pkgs` in your `PATH`.

## Contributers

This script was developed by [myself](https://github.com/br0ns) and
[Idolf](https://github.com/idolf).
