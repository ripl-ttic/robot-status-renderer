add_definitions(-std=gnu99)

add_library(robot-status-renderer SHARED
            renderer_robot_status.c)

target_link_libraries(robot-status-renderer ${OPENGL_LIBRARIES})

set(REQUIRED_LIBS bot2-vis lcmtypes_robot-status)

pods_use_pkg_config_packages(robot-status-renderer ${REQUIRED_LIBS})

pods_install_headers(renderer_robot-status.h DESTINATION
                     robot-status_renderer)

pods_install_libraries(robot-status-renderer)
pods_install_pkg_config_file(robot-status-renderer
    CFLAGS
    LIBS -lrobot-status-renderer
    REQUIRES ${REQUIRED_LIBS}
    VERSION 0.0.1)
