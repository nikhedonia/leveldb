cxx_library(
  name = 'leveldb',
  licenses = [
    'LICENSE',
  ],
  header_namespace = '',
  exported_headers = subdir_glob([
    ('include', 'leveldb/**/*.h'),
  ]),
  headers = subdir_glob([
    ('', 'db/**/*.h'),
    ('', 'helpers/**/*.h'),
    ('', 'port/**/*.h'),
    ('', 'table/**/*.h'),
    ('', 'util/**/*.h'),
  ]),
  srcs = glob([
    'db/**/*.cc',
    'helpers/**/*.cc',
    'table/**/*.cc',
    'util/**/*.cc',
    'port/**/*.cc',
  ], 
  excludes = [
    '**/*_test.cc',
    '**/testharness.cc',
    '**/testutil.cc',
  ]),
  compiler_flags = [
    '-std=c++11',
  ],
  platform_compiler_flags = [
    ('default', ['-DOS_MACOSX', '-fno-builtin-memcmp', '-DLEVELDB_PLATFORM_POSIX', '-DLEVELDB_ATOMIC_PRESENT']),
    ('^macos.*', ['-DOS_MACOSX', '-fno-builtin-memcmp', '-DLEVELDB_PLATFORM_POSIX', '-DLEVELDB_ATOMIC_PRESENT']),
    ('^linux.*', ['-DOS_LINUX']),
    ('^windows.*', ['-lpthread', '-DOS_LINUX', '-DCYGWIN']),
  ],
  visibility = [
    'PUBLIC',
  ],
)

cxx_binary(
  name = 'autocompact-test',
  headers = subdir_glob([
    ('', 'db/**/*.h'),
    ('', 'helpers/**/*.h'),
    ('', 'port/**/*.h'),
    ('', 'table/**/*.h'),
    ('', 'util/**/*.h'),
  ]),
  srcs = [
    'db/autocompact_test.cc',
  ],
  compiler_flags = [
    '-std=c++11',
  ],
  platform_compiler_flags = [
    ('default', ['-DOS_MACOSX', '-fno-builtin-memcmp', '-DLEVELDB_PLATFORM_POSIX', '-DLEVELDB_ATOMIC_PRESENT']),
  ],
  deps = [
    ':leveldb',
  ],
)
