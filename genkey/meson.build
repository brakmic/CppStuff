project('genkey', 'cpp',
  version : '1.0',
  default_options : ['warning_level=3',
                     'cpp_std=c++11'])


libbitcoin = dependency('libbitcoin')
gmp_inc = include_directories('/usr/local/opt/gmp/include')
libgmp = declare_dependency(link_args : '-lgmp', include_directories : gmp_inc)

exe = executable('genkey', 'genkey.cpp',
  install : true, dependencies: [libgmp, libbitcoin])

test('basic', exe)
