###################################################################
###                                                             ###
### file:       test/meson.build                                ###
### brief:      test meson build file                           ###    
### version:    0.5.2-meson                                     ###
### licence:    see accompanying LICENSE file [MIT]             ###
### copyright:  Jonathan Guzmán <jonguz5@hotmail.com>  2022.    ###
### date:       01/02/2021                                      ###
###                                                             ###
###################################################################

restclient_cpp_tests_srcs = [
    'test_connection.cc',
    'test_helpers.cc',
    'test_restclient.cc',
    'tests.cpp'
]

restclient_cpp_tests_inc = []
restclient_cpp_tests_deps = [
    restclient_cpp_dep,
    gtest_dep,
    nlohmann_json_dep,
]
restclient_cpp_tests_args = []

testexe = executable('testexe', restclient_cpp_tests_srcs,
                     #include_directories : libcpprequests_inc,
                     #link_with : libcpprequests_test_lib,
                     dependencies: restclient_cpp_tests_deps)

test('restclient-cpp unit tests', testexe, args: restclient_cpp_tests_args)