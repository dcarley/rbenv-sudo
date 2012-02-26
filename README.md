# rbenv-sudo

rbenv-sudo is a plugin for rbenv that allows you to run rbenv-provided
Rubies and Gems from within a `sudo` session.

## Implementation

It does so by prepending rbenv's `bin/` and `shims/` directories to a
hardcoded representation of root's `$PATH`. It differs from `rvmsudo` in
that it doesn't pass your present `$PATH` or any other environment
variables over to the sudo session, in the hope of damage limitation.

It will function with the common sudo configuration of:

        Defaults env_reset, secure_path

rbenv-sudo should still be used with some caution. Bear in mind that any
Rubies, Gems or other binary shims, could maliciously take precedence over
system binaries of the same name.

## Installation

1. Setup [rbenv](https://github.com/sstephenson/rbenv)
1. Make sure you have a plugins directory:

        mkdir ~/.rbenv/plugins

1. Clone `rbenv-sudo` into the plugins directory:

        clone git://github.com/dcarley/rbenv-sudo.git ~/.rbenv/plugins/rbenv-sudo

## Usage

Prefix your use of sudo with the `rbenv` command:

        $ rbenv sudo chef-solo --version
        Chef: 0.10.8
        $ rbenv sudo ruby --version
        ruby 1.9.3p0 (2011-10-30 revision 33570) [x86_64-linux]
        $ rbenv sudo ruby -e "puts Process.uid"
        0

## License

This code is provided under the MIT license.
