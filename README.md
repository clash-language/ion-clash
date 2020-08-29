# Ion-Clash

To expedite the prototyping process of the Clash hybrid compiler and a proper shell, this repository
stands on the shoulders of Ion, *"a modern system shell that features a simple, yet powerful, syntax. 
It is written entirely in Rust, which greatly increases the overall quality and security of the shell. 
It also offers a level of performance that exceeds that of Dash, when taking advantage of Ion's features. While it
is developed alongside, and primarily for, RedoxOS, it is a fully capable on other \*nix platforms.*""

Since Clash aims to combine language and shell with the capability to integrate with Bash 5.0 and PowerShell, 
it makes sense to bootstrap a fork of Ion before the Clash language is self-hoisted. 

# Ion Specification

Ion has a RFC process for language proposals. Ion's formal specification is located within the
[rfcs](https://gitlab.redox-os.org/redox-os/ion/tree/rfcs) branch. The RFC process is still in
the early stages of development, so much of the current and future implementation ideas have
yet to be written into the specification.

# Ion Manual


[The Ion manual online](https://doc.redox-os.org/ion-manual/html) 
is generated automatically on each commit via [mdBook](https://github.com/azerupi/mdBook) and hosted on Redox OS's website.

**Building the manual for local reference**

Sources for the manual are located in the `manual` directory.

You can build the manual using
```sh
make manual
mdbook build -d ../public manual
```

# Ion library example
See the [examples folder](https://gitlab.redox-os.org/redox-os/ion/tree/master/examples) and the [Parallelion project](https://gitlab.redox-os.org/AdminXVII/parallelion)

# Developer set up

Those who are developing software with Rust should install the [Rustup toolchain manager](https://rustup.rs/).
After installing rustup, run `rustup override set 1.39.0` to set your Rust toolchain to the version that Ion is
targeting at the moment. To build for Redox OS, `rustup override set nightly` is required to build the Redox
dependencies.

# Build dependencies

Please ensure that both cargo and rustc 1.39.0 or higher is installed for your system.
Release tarballs have not been made yet due to Ion being incomplete in a few remaining areas.

# Compile instructions for distribution

```sh
git clone https://gitlab.redox-os.org/redox-os/ion/
cd ion
RUSTUP=0 make # By default RUSTUP equals 1, which is for developmental purposes
sudo make install prefix=/usr
sudo make update-shells prefix=/usr
```

> To compile in DEBUG mode, pass `DEBUG=1` as an argument to `make`
