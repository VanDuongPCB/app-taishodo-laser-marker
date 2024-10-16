project(LaserMarker)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

file(GLOB HEADER_FILES *.h)
file(GLOB SRC_FILES *.cpp)
file(GLOB UI_FILES *.ui)
file(GLOB RESOURCE_FILES *.qrc)

source_group("Form Files" FILES ${UI_FILES} ${RESOURCE_FILES})

add_executable(${PROJECT_NAME} WIN32 ${HEADER_FILES} ${SRC_FILES} ${UI_FILES} ${RESOURCE_FILES})

find_package(Qt${QT_VERSION_NUMBER} COMPONENTS Core Widgets Network SerialPort REQUIRED)


target_link_libraries(${PROJECT_NAME}
Qt${QT_VERSION_NUMBER}::Core
Qt${QT_VERSION_NUMBER}::Widgets
Qt${QT_VERSION_NUMBER}::Network
Qt${QT_VERSION_NUMBER}::SerialPort
)


# if(MSVC)
#     # Set the "VC++ Directories > Include Directories" setting
#     set(CMAKE_VS_SDK_INCLUDE_DIRECTORIES 
#     "$(VC_IncludePath);$(WindowsSDK_IncludePath)" 
#     "${CMAKE_SOURCE_DIR}/CommonUI/FxCommonUI"
#     "${CMAKE_SOURCE_DIR}/Licensing/FxLicensing"
#     )
# endif()


# target_include_directories(${PROJECT_NAME} PUBLIC 
# ${CMAKE_SOURCE_DIR}/CommonUI/FxCommonUI
# )


set_target_properties(
    ${PROJECT_NAME}
    PROPERTIES
    FOLDER "Apps"
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}"
)