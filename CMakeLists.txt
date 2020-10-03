cmake_minimum_required(VERSION 3.1)
project(get_openweather_data C)

find_package(OpenSSL REQUIRED)
find_package(PkgConfig REQUIRED)

pkg_check_modules(JSONC REQUIRED json-c)
include_directories(${JSONC_INCLUDE_DIRS})

add_library(http_connector ./libhttp_connector/src/http_connector.c)
target_link_libraries(http_connector OpenSSL::SSL)
if(MINGW)
  target_link_libraries(http_connector wsock32 ws2_32)
endif(MINGW)

add_library(openweathermap_client ./src/openweather.c)
target_link_libraries(openweathermap_client http_connector)
target_link_libraries(openweathermap_client ${JSONC_LIBRARIES})

