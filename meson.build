project('restclient-cpp',
  'cpp',
  default_options : [
    'cpp_std=c++14',
    'buildtype=release'
  ],
  license: ['MIT'],
  version: '0.5.2',
  meson_version: '>=0.55.0'
)

# version configuration

restclient_cpp_version = meson.project_version()
restclient_cpp_libversion = restclient_cpp_version

# library definition

## dependencies

### Google Test
gtest_dep = dependency(
                'gtest',
                fallback: ['gtest', 'gtest_dep']
)
### - threads
threads_dep = dependency('threads')
### - CURL
curl_dep = dependency('libcurl', version : '>= 7.81.0')
### - jsoncpp
jsoncpp_dep = dependency(
                'jsoncpp',
                fallback: ['jsoncpp', 'jsoncpp_dep'],
                required: false)


## restclient-cpp dependency

subdir('restclient-cpp')

restclient_cpp_dep = declare_dependency(
    link_with: restclient_cpp_lib,
    include_directories: restclient_cpp_inc
)

pkgconfig = import('pkgconfig')
pkgconfig.generate(restclient_cpp_lib,
  name: 'restclient-cpp',
  filebase: 'restclient-cpp',
  description: 'REST client for C++',
  version: restclient_cpp_libversion,
  url: 'http://code.mrtazz.com/restclient-cpp')


# Unit Tests

restclient_cpp_tests_srcs = [
    'vendor/jsoncpp-0.10.5/dist/jsoncpp.cpp',
    'test/test_connection.cc',
    'test/test_helpers.cc',
    'test/test_restclient.cc',
    'test/tests.cpp'
]

restclient_cpp_tests_inc = [
  include_directories('vendor/jsoncpp-0.10.5/dist/'),
]
restclient_cpp_tests_deps = [
    restclient_cpp_dep,
    gtest_dep,
]

restclient_cpp_tests_args = [
  '-DJSONDLL',
]

testexe = executable('testexe', restclient_cpp_tests_srcs,
                     #include_directories : libcpprequests_inc,
                     #link_with : libcpprequests_test_lib,
                     dependencies: restclient_cpp_tests_deps)

test('restclient-cpp unit tests', testexe, args: restclient_cpp_tests_args)