project('zlib', 'c', version : '1.2.11', license : 'zlib')

link_args = []

cc = meson.get_compiler('c')

if cc.get_id() == 'gcc' and host_machine.system() == 'linux'
  vflag = '-Wl,--version-script,@0@/zlib.map'.format(meson.current_source_dir())
  link_args += [vflag]
endif

src = ['adler32.c', 'crc32.c', 'deflate.c', 'infback.c', 'inffast.c', 'inflate.c',
'inftrees.c', 'trees.c', 'zutil.c',
'compress.c', 'uncompr.c', 'gzclose.c', 'gzlib.c', 'gzread.c', 'gzwrite.c']

zlib = library('z', src,
  c_args : ['-DZLIB_DLL'],
  link_args : link_args,
  install : true,
  version : meson.project_version())

incdir = include_directories('.')

zlib_dep = declare_dependency(link_with : zlib,
  include_directories : incdir)
