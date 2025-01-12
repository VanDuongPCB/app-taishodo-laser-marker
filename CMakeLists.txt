cmake_minimum_required(VERSION 3.5)

set(PRODUCT_NAME "Laser Marker" CACHE STRING "Default name of this production." )

project(PcbLaserMarker)

set(QT_VERSION_NUMBER 6 CACHE STRING "Default QT version" )
set(QT_DIR "" CACHE PATH "Path to QT")

IF(NOT EXISTS ${QT_DIR})
message(SEND_ERROR "QT_DIR does not exist.")
ENDIF(NOT EXISTS ${QT_DIR})


set_property(GLOBAL PROPERTY USE_FOLDERS TRUE)

foreach( OUTPUTCONFIG ${CMAKE_CONFIGURATION_TYPES} )
    string( TOUPPER ${OUTPUTCONFIG} OUTPUTCONFIG )
    set( CMAKE_RUNTIME_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
    set( CMAKE_LIBRARY_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
    set( CMAKE_ARCHIVE_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
    set( RUNTIME_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
    set( LIBRARY_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
    set( ARCHIVE_OUTPUT_DIRECTORY_${OUTPUTCONFIG} ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
    set( RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
    set( LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
    set( ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${PRODUCT_NAME} )
endforeach( OUTPUTCONFIG CMAKE_CONFIGURATION_TYPES )

add_subdirectory(Apps)
add_subdirectory(Devices)
add_subdirectory(Kernel)
add_subdirectory(Widgets)



