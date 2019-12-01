## A simple Bitcoin Address generator based on [libbitcoin](https://github.com/libbitcoin)

### Compilation

This C++ project uses [Meson](https://mesonbuild.com/Getting-meson.html) for building.

Some extra work was needed to link [GMP](https://gmplib.org/) (GNU multiple precision arithmetic library).

As this library offers no pkg-config, I had to manually declare its path and includes.

However, you will have to adapt the **include_directories** path for your OS.

```
gmp_inc = include_directories('/usr/local/opt/gmp/include')
libgmp = declare_dependency(link_args : '-lgmp', include_directories : gmp_inc)
```

Then put it like any 'normal' library in the dependencies list:

```
exe = executable('genkey', 'genkey.cpp',
  install : true, dependencies: [libgmp, libbitcoin])
```

To setup a new build directory type `meson build`.

Then compile the project with [Ninja](https://github.com/ninja-build/ninja).

```
ninja -C build
```

Start the program with `./build/genkey`



