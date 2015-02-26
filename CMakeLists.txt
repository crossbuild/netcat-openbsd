#
# Cmake Build script for netcat-openbsd 
# Author : Cristian Rodríguez <crrodriguez@suse.de>
#
# Copyright (c) 2008 SUSE LINUX Products GmbH, Nuernberg, Germany.
# This file and all modifications and additions to the pristine
# package are under the same license as the package itself.
#
# Please submit bugfixes or comments via http://bugs.opensuse.org/

PROJECT(netcat-openbsd C)
SET(CMAKE_VERBOSE_MAKEFILE ON)
SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=gnu99 -fvisibility=hidden -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -g -W -Wall")


INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/openbsd-compat)

SET(NETCAT_SRCS netcat.c atomicio.c socks.c openbsd-compat/base64.c openbsd-compat/readpassphrase.c)
ADD_EXECUTABLE(nc ${NETCAT_SRCS})
INSTALL(PROGRAMS nc DESTINATION bin)
INSTALL(FILES nc.1 DESTINATION share/man/man1)
