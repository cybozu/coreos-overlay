Modifications made:

- drop python updater, eselect stuff

- drop src_test, test use flags

- renamed one patch in PATCHES variable, so I don't need to rename the
  file (it was using `${PN}`, which in `dev-lang/python` expands to
  `python`, whereas in `dev-lang/python-oem` it would expand to
  `python-oem`).

- drop examples, gdbm, libressl, ncurses, sqlite, ssl, tk, wininst

- remove, but enable build, ipv6, threads

- drop xml use flag, but keep the internal copies of expat, do not
  disable _elementtree and pyexpat modules and tell the configure
  script to use the internal stuff

- also keep using internal libffi, instead of depending on libffi

- move RDEPEND to DEPEND, so RDEPEND remains empty

- add --prefix=/usr/share/oem/python to the myeconfargs variable

- change --enable-shared to --disable-shared

- set mandir, infodir and includedir to some subdirectory of /discard,
  so during installation this could be easily removed

- export some configure variables for the cross-compilation:
  ac_cv_file__dev_ptc and ac_cv_file__dev_ptmx. If not done, build
  will fail with a message saying that these should be set to either
  yes or no.

- simplify src_install:

  - replace the hardcoded ${ED}/usr/bin with bindir variable set to
    ${ED}/usr/share/oem/python/bin

  - create a versionless link to python executable

  - drop sed stuff mucking with LDFLAGS

  - drop collision fixes

  - drop ABIFLAGS hack

  - do not install ACKS, HISTORY and NEWS files

  - drop gdb autoload stuff

  - drop pydoc.{conf,init} stuff

  - drop python-exec stuff

  - remove installed stuff in /discard
