cmake_minimum_required(VERSION 3.0.0)
project(polipo VERSION 0.1.0)

include(CTest)
enable_testing()

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=c11")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Os -g -Wall -fno-strict-aliasing")

set(HEADERS
atom.h auth.h chunk.h client.h config.h dirent_compat.h diskcache.h
dns.h event.h forbidden.h fts_compat.h ftsimport.h http_parse.h http.h
io.h local.h log.h md5.h mingw.h object.h parse_time.h polipo.h
server.h socks.h tunnel.h util.h
)

set(SRCS  
util.c event.c io.c chunk.c atom.c object.c log.c diskcache.c main.c 
config.c local.c http.c client.c server.c auth.c tunnel.c 
http_parse.c parse_time.c dns.c forbidden.c 
md5.c ftsimport.c fts_compat.c socks.c mingw.c)

add_executable(polipo ${SRCS} ${HEADERS})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)