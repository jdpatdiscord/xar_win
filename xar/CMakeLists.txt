cmake_minimum_required(VERSION 3.15)

project(xar LANGUAGES C)

find_package(LibXml2 REQUIRED)

add_library(xar STATIC
    lib/archive.c
    lib/arcmod.c
    lib/b64.c
    lib/darwinattr.c
    lib/data.c
    lib/ea.c
    lib/err.c
    lib/ext2.c
    lib/fbsdattr.c
    lib/filetree.c
    lib/hash.c
    lib/io.c
    lib/linuxattr.c
    lib/lzmaxar.c
    lib/macho.c
    lib/script.c
    lib/signature.c
    lib/stat.c
    lib/subdoc.c
    lib/util.c
    lib/zxar.c
    src/xar.c
    )

target_compile_definitions(xar PUBLIC
    DEV_HEXSTRING=PRIx32
    DEV_CAST="(uint32_t)"
    DEV_STRING=PRId32
    INO_HEXSTRING=PRIx64
    INO_CAST="(uint64_t)"
    INO_STRING=PRId64
    XAR_NUMERIC_VERSION=0x01060180
    XAR_VERSION_NUM=0x01060180
    XAR_VERSION="1.6.1"
    )

target_include_directories(xar PUBLIC
    lib/
    src/)

target_link_libraries(xar PUBLIC
    LibXml2::LibXml2
    )