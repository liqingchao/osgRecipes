FIND_PATH(ASSIMP_INCLUDE_DIR assimp/ai_assert.h)
FIND_LIBRARY(ASSIMP_LIBRARY assimp)
FIND_LIBRARY(ASSIMP_ZLIB_LIBRARY zlib)
OPTION(ASSIMP_USE_STATIC "Link with static version of AssImp" OFF)

IF(ASSIMP_INCLUDE_DIR AND ASSIMP_LIBRARY)
    SET(EXTERNAL_INCLUDE_DIR ${ASSIMP_INCLUDE_DIR})
    IF(NOT ASSIMP_USE_STATIC)
        ADD_DEFINITIONS(-DASSIMP_DLL)
        SET(EXTERNAL_LIBRARIES ${ASSIMP_LIBRARY})
    ELSE(NOT ASSIMP_USE_STATIC)
        SET(EXTERNAL_LIBRARIES ${ASSIMP_LIBRARY} ${ASSIMP_ZLIB_LIBRARY})
    ENDIF(NOT ASSIMP_USE_STATIC)
    
    SET(LIBRARY_NAME osgdb_assimp)
    SET(LIBRARY_FILES ReaderWriterAssImp.cpp)
    START_LIBRARY()
ENDIF(ASSIMP_INCLUDE_DIR AND ASSIMP_LIBRARY)
