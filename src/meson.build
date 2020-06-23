project(
  'purge_dups',
  ['c'],
  version : '1.0.1',
  default_options : [
    'buildtype=release',
    'warning_level=3',
    'c_std=c11',
    'b_ndebug=if-release'],
  license : 'MIT',
  meson_version : '>= 0.46.0')

cflags = '-Wall'

# libm
cc = meson.get_compiler('c')
m_dep = cc.find_library('m', required : true)

# libz
zlib_dep = dependency('zlib', required : true)

lib_deps = [zlib_dep, m_dep]

c_sources = files([
    'asset.c',
    'bamlite.c',
    'cov.c',
    'opt.c',
    'paf.c',
    'sdict.c',
])

lib = static_library(
  'purge_dups_lib',
  c_sources,
  dependencies : lib_deps,
  c_args : cflags)

if not meson.is_subproject()
  executable(
    'purge_dups',
    files([
        'purge_dups.c',
    ]),
    install : true,
    dependencies : lib_deps,
    link_with : lib,
    #include_directories : ['.'],
    c_args : cflags,
  )
  executable(
    'purge_dups_calcuts',
    files([
        'calcuts.c',
    ]),
    install : true,
    dependencies : lib_deps,
    link_with : lib,
    c_args : cflags,
  )
  executable(
    'purge_dups_get_seqs',
    files([
        'get_seqs.c',
    ]),
    install : true,
    dependencies : lib_deps,
    link_with : lib,
    c_args : cflags,
  )
  executable(
    'purge_dups_ngscstat',
    files([
        'ngscstat.c',
    ]),
    install : true,
    dependencies : lib_deps,
    link_with : lib,
    c_args : cflags,
  )
  executable(
    'purge_dups_pbcstat',
    files([
        'pbcstat.c',
    ]),
    install : true,
    dependencies : lib_deps,
    link_with : lib,
    c_args : cflags,
  )
  executable(
    'purge_dups_split_fa',
    files([
        'split_fa.c',
    ]),
    install : true,
    dependencies : lib_deps,
    link_with : lib,
    c_args : cflags,
  )
endif
