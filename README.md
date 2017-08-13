# Alien::Build::Plugin::Build::Make [![Build Status](https://secure.travis-ci.org/plicease/Alien-Build-Plugin-Build-Make.png)](http://travis-ci.org/plicease/Alien-Build-Plugin-Build-Make)

Make plugin for Alien::Build

# SYNOPSIS

    use alienfile;
    # For a recipe that requires GNU Make
    plugin 'Build::Make' => 'gmake';

# DESCRIPTION

By default [Alien::Build](https://metacpan.org/pod/Alien::Build) provides a helper for the `make` that is used by Perl and [ExtUtils::MakeMaker](https://metacpan.org/pod/ExtUtils::MakeMaker) itself.
This is handy, because it is the one make that you can mostly guarantee that you will have.  Unfortunately it may be
a `make` that isn't supported by the library or tool that you are trying to alienize.  This is mostly a problem on
Windows, where the supported `make`s for years were Microsoft's `nmake` and Sun's `dmake`, which many open source
projects do not use.  This plugin will alter the [alienfile](https://metacpan.org/pod/alienfile) recipe to use a different `make`.  It may (as in the
case of `gmake` / [Alien::gmake](https://metacpan.org/pod/Alien::gmake)) automatically download and install an alienized version of that `make` if it
is not already installed.

This plugin should NOT be used with other plugins that replace the `make` helper, like 
[Alien::Build::Plugin::Build::CMake](https://metacpan.org/pod/Alien::Build::Plugin::Build::CMake), [Alien::Build::Plugin::Build::Autoconf](https://metacpan.org/pod/Alien::Build::Plugin::Build::Autoconf), 
[Alien::Build::Plugin::Build::MSYS](https://metacpan.org/pod/Alien::Build::Plugin::Build::MSYS).  This plugin is intended instead for projects that use vanilla makefiles of
a specific type.

This plugin is for now distributed separately from [Alien::Build](https://metacpan.org/pod/Alien::Build), but the intention is for it to soon become
a core plugin for [Alien::Build](https://metacpan.org/pod/Alien::Build).

# PROPERTIES

## make\_type

The make type needed by the [alienfile](https://metacpan.org/pod/alienfile) recipe:

- dmake

    Sun's dmake.

- gmake

    GNU Make.

- nmake

    Microsoft's nmake.  It comes with Visual C++.

- umake

    Any UNIX `make`  Usually either BSD or GNU Make.

# HELPERS

## make

    %{make}

This plugin may change the make helper used by your [alienfile](https://metacpan.org/pod/alienfile) recipe.

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
