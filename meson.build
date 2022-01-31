###################################################################
###                                                             ###
### file:       meson.build                                     ###
### brief:      root meson build file                           ###    
### version:    0.5.2-meson                                     ###
### licence:    see accompanying LICENSE file [MIT]             ###
### copyright:  Jonathan Guzmán <jonguz5@hotmail.com>  2022.    ###
### date:       31/01/2021                                      ###
###                                                             ###
###################################################################

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

if get_option('build_tests')
    ### Google Test
    gtest_dep = dependency(
                    'gtest',
                    fallback: ['gtest', 'gtest_dep']
    )
    ### - jsoncpp
    jsoncpp_dep = dependency(
                    'jsoncpp',
                    fallback: ['jsoncpp', 'jsoncpp_dep'],
                    required: false)
else
    message('Skipping tests dependencies')
endif


### - threads
threads_dep = dependency('threads')
### - CURL
curl_dep = dependency('libcurl', version : '>= 7.81.0')



## restclient-cpp dependency

subdir('restclient-cpp')


restclient_cpp_dep = declare_dependency(
    link_with: restclient_cpp_lib,
    include_directories: restclient_cpp_inc
)


if get_option('build_tests')
    subdir('test')
else
    message('Skipping tests')
endif


pkgconfig = import('pkgconfig')
pkgconfig.generate(restclient_cpp_lib,
  name: 'restclient-cpp',
  filebase: 'restclient-cpp',
  description: 'REST client for C++',
  version: restclient_cpp_libversion,
  url: 'http://code.mrtazz.com/restclient-cpp')
