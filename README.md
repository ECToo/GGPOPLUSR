# GGAC+R GGPO-BASED CASTER

A netplay implementation and quality-of-life tool bundle for the Steam release
of _Guilty Gear XX Accent Core +R_.

## Table of contents
  * [Getting Started](#getting-started)
  * [Why GGPO? Why +R? Why now?](#why-ggpo-why-r-why-now)
  * [Contributing](#contributing)
  * [Authors](#authors)
  * [License](#license)
  * [External Licenses and Copyright Information](#external-licenses-and-copyright-information)

## Getting Started

GGPOPLUSR relies on [GGPO](https://github.com/pond3r/ggpo) for its netplay
library, and Microsoft's [Detours](https://github.com/microsoft/Detours)
to install custom netplay hooks at runtime. For players, GGPO and Detours
will be distributed with the GGPOPLUSR releases, but for developers,
you'll need to check out and build GGPO and Detours separately.

GGPOPLUSR relies on [ValveFileVDF](https://github.com/TinyTinni/ValveFileVDF)
to parse Steam's configuration files to automatically detect your GGXXACPR
installation. Developers will need a checkout- or at least a copy of the
main header file- to build GGPOPLUSR.

Many development tools also rely on [Python 3](https://www.python.org/).
While it's not strictly necessary, developers may find it useful to have
Python installed and available from their system path, particularly for
prototyping new tools.

GGPOPLUSR uses [CMake](https://cmake.org/) as a build engine. This is
completely irrelevant to players, but developers will need an installation
of CMake, or IDE support for CMake, like Visual Studio.

Most developers will also need reverse engineering tools of some kind. We
recommend [CheatEngine](https://github.com/cheat-engine/cheat-engine),
[x64dbg](https://github.com/x64dbg/x64dbg),
[Ghidra](https://github.com/NationalSecurityAgency/ghidra),
or any combination of the three.

To build and run GGPOPLUSR:
1. Clone and build Detours, GGPO, and ValveFileVDF using x86-compatible build
   tools.
   - GGXXAC+R is natively compiled for 32-bit x86, and using an entire 32-bit
     toolchain prevents us from needing to handle cross compilation.
2. Use Visual Studio (or your preferred CMake generator) to generate a new
   CMake cache.
   - Remember to add your Detours build output as a `DETOURS_DIR` CMake
     variable, and your ValveFileVDF checkout as a `VALVEFILEVDF_DIR`
     CMake variable.
3. Build the launcher using the makefile or project generated by CMake.
4. Confirm that `Launcher.exe` and `Sidecar.dll` are in the build output.
5. Run `Launcher.exe`.

## Why GGPO? Why +R? Why now?
While lockstep netcode was considered industry standard for many years
(including triple-A titles like _Street Fighter IV_), its failures have
been severe and widespread (_Ultimate Marvel vs. Capcom 3_ and _King of
Fighters XIII_).

In the last decade, many prominent fighting-game developers have documented
the negative player effects that lockstep netcode and its necessary input
latency create. Instead, developers and community members alike have
espoused the virtues of rollback-based netcode, including
[MikeZ of Lab Zero and Skullgirls](https://mikezsez.blogspot.com/2019/11/lets-talk-about-rollbacks.html),
[Michael Stallone of Netherrealm and Mortal Kombat](https://youtu.be/7jb0FOcImdg),
and [Adam "Keits" Heart of Iron Galaxy and Killer Instinct](https://twitter.com/thekeits/status/1143897723848003584?lang=en).

GGXXAC+R uses an engine that was built on lockstep netcode, before
rollback-based netcode became more common in fighting games.

While in some cases +R's netcode can hold up relatively well, playing with
community members from across a country (or across an ocean!) is a
poor experience. Fortunately, thanks to GGPO's open-source release in October
2019, adapting a game to rollback-based netcode no longer requires modifying
the game _and_ writing an entire netcode implementation. This opens up the
possibility for fighting games new and old to be brought up to a new gold
standard- including this project.

## Contributing

Contributions of all kinds are welcome! While we're certainly seeking help
with C++ development, x86 assembly, Win32 APIs, reverse engineering, and
networking code, we need many non-technical skills as well! **You, the reader,**
can help us directly by:

* Reading [CONTRIBUTING.md](https://github.com/adanducci/GGPOPLUSR/blob/master/CONTRIBUTING.md)
  and submitting new pull requests
* Updating and organizing the [wiki](https://github.com/adanducci/GGPOPLUSR/wiki)
* Testing early-access releases and reporting issues on the
  [issue tracker](https://github.com/adanducci/GGPOPLUSR/issues/new)
* Contribute to reverse engineering, identify bugs, or just chat on our
  [Discord](https://discord.gg/CgvvgDU)
* Spreading the word and recruiting new players and contributors!

## Authors

Authors

* @Labreezy - founder
* @WesselKuipers
* @adanducci

See also the [list of contributors](https://github.com/adanducci/GGPOPLUSR/contributors)
who participated in this project.

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.

## External Licenses and Copyright Information

Guilty Gear, Guilty Gear XX, and all related software
Copyright � Arc System Works.

Steam
Copyright � 2019 Valve Corporation.

Detours
Copyright � Microsoft Corporation.

GGPO (Good Game Peace Out)
Copyright � GroundStorm Studios, LLC.

ValveFileVDF
Copyright � Matthias M�ller.

CMake - Cross Platform Makefile Generator
Copyright � 2000-2019 Kitware, Inc. and Contributors.
