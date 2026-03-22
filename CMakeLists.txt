cmake_minimum_required(VERSION 3.15)
project(Update C CXX)

list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake")

set(CMAKE_INSTALL_SYSTEM_RUNTIME_DESTINATION ".")

add_library(lua STATIC
    src/lua/lapi.c
    src/lua/lapi.h
    src/lua/lauxlib.c
    src/lua/lauxlib.h
    src/lua/lbaselib.c
    src/lua/lcode.c
    src/lua/lcode.h
    src/lua/ldblib.c
    src/lua/ldebug.c
    src/lua/ldebug.h
    src/lua/ldo.c
    src/lua/ldo.h
    src/lua/ldump.c
    src/lua/lfunc.c
    src/lua/lfunc.h
    src/lua/lgc.c
    src/lua/lgc.h
    src/lua/linit.c
    src/lua/liolib.c
    src/lua/llex.c
    src/lua/llex.h
    src/lua/llimits.h
    src/lua/lmathlib.c
    src/lua/lmem.c
    src/lua/lmem.h
    src/lua/loadlib.c
    src/lua/lobject.c
    src/lua/lobject.h
    src/lua/lopcodes.c
    src/lua/lopcodes.h
    src/lua/loslib.c
    src/lua/lparser.c
    src/lua/lparser.h
    src/lua/lstate.c
    src/lua/lstate.h
    src/lua/lstring.c
    src/lua/lstring.h
    src/lua/lstrlib.c
    src/lua/ltable.c
    src/lua/ltable.h
    src/lua/ltablib.c
    src/lua/ltm.c
    src/lua/ltm.h
    src/lua/lua.h
    src/lua/luaconf.h
    src/lua/lualib.h
    src/lua/lundump.c
    src/lua/lundump.h
    src/lua/lvm.c
    src/lua/lvm.h
    src/lua/lzio.c
    src/lua/lzio.h
)


if (CMAKE_SYSTEM_NAME MATCHES "Linux")
    target_compile_definitions(lua PRIVATE LUA_USE_MKSTEMP=1)
endif ()

set(UPDATE_SOURCES
    "src/main.cpp"
    "src/lua.rc"
)

if (WIN32)
    add_executable(Update WIN32 ${UPDATE_SOURCES})
else ()
    add_executable(Update ${UPDATE_SOURCES})
endif ()

target_link_libraries(Update PRIVATE lua)
