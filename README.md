# Environments

This is a set of scripts designed to get a particular environment up and
running with minimal effort.

__Warning: these scripts make fundamental changes to your system.  Please read
the scripts in `bin` and understand what they do before running them__

## Install

### OSX Development Environment

First, install [GCC for OS X](https://github.com/kennethreitz/osx-gcc-installer) (requires OS X 10.6 or higher).

Set up your ssh keys and run the script:

    ssh-keygen -t rsa
    bash < <(curl -s https://raw.github.com/SeenHub/environments/master/bin/osx-development)

### Ubuntu Server Environment

First, log in as root and run:

    bash < <(curl -s https://raw.github.com/SeenHub/environments/master/bin/ubuntu-server-root)

Next, add the relevant public keys for `root`.

Then:

    su deploy
    bash < <(curl -s https://raw.github.com/SeenHub/environments/master/bin/ubuntu-server-deploy)

Finally, add the relevant public keys for `deploy`.
