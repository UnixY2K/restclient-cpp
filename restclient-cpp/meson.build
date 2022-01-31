###################################################################
###                                                             ###
### file:       restclient-cpp/meson.build                      ###
### brief:      library meson build file                        ###    
### version:    0.5.2-meson                                     ###
### licence:    see accompanying LICENSE file [MIT]             ###
### copyright:  Jonathan Guzmán <jonguz5@hotmail.com>  2022.    ###
### date:       31/01/2021                                      ###
###                                                             ###
###################################################################

restclient_cpp_inc = include_directories('include')

restclient_cpp_srcs = [
    'src/restclient.cc',
    'src/connection.cc',
    'src/helpers.cc'
]
restclient_cpp_args = []
restclient_cpp_link = []
restclient_cpp_deps = [
    threads_dep,
    curl_dep,
]

restclient_cpp_lib = library('restclient-cpp',
                        restclient_cpp_srcs,
                        include_directories: restclient_cpp_inc,
                        cpp_args: restclient_cpp_args,
                        dependencies: restclient_cpp_deps,
                        version: restclient_cpp_libversion)
