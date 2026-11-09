# freebsd-sysroot

**Superseded** by one package per identity: `xim:x86_64-freebsd-sysroot` and
`xim:aarch64-freebsd-sysroot`. The release here carries an earlier manifest form that
no mcpp release reads; it is kept unchanged.

Release storage for `xim:freebsd-sysroot`: the FreeBSD base system a program is
compiled and linked against -- `usr/include`, the shared libraries, the dynamic
loader, crt objects and the static archives of the C library, the C++ run-time
and the compiler run-time -- for amd64 and arm64, with libc++'s std module
sources generated from the official libcxx source release of the base's libc++
version (FreeBSD installs none).

The payload is target code and host-independent: one archive serves every host.
It is a base package (mcpp design 2026-11-10 E5): `mcpp.toml` at its top maps each
architecture to its sysroot and states the layers it supplies.

    freebsd-sysroot-<ver>/
      mcpp.toml  PROVENANCE.md
      amd64/  arm64/                one sysroot per architecture
        usr/share/libc++/v1/        std.cppm, std.compat.cppm

Assembled from the official `base.txz` distribution sets (download.freebsd.org)
by `openxlings/xim-pkgindex`: `.agents/tools/build-freebsd-sysroot.py`.
PROVENANCE.md in the archive names each upstream set and its sha256.
