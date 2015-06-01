cmake_minimum_required(VERSION 2.8.3)
project(mongo_cxx_driver)

add_custom_target(client)
add_custom_command(TARGET client COMMAND "scons" ARGS "--sharedclient -C${CMAKE_CURRENT_SOURCE_DIR}")

install(CODE "execute_process(COMMAND scons --prefix=\$ENV{DESTDIR}/\${CMAKE_INSTALL_PREFIX} --sharedclient -C${CMAKE_CURRENT_SOURCE_DIR} install)")

install(FILES package.xml DESTINATION share/mongo_cxx_driver)
