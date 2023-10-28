cmake_minimum_required(VERSION 3.5)
project(application)

cmake_policy(SET CMP0071 NEW)
set(CMAKE_CXX_STANDARD 20 CACHE STRING "c++ version to use" FORCE)
set(CMAKE_CXX_EXTENSIONS ON CACHE BOOL "use gnu++" FORCE)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(application application.cpp)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)
find_package(Qt6 REQUIRED COMPONENTS Core Gui Quick)
# otherwise the qrc path would be qrc:/ui/ui/main.qml
set_source_files_properties(ui/main.qml PROPERTIES QT_RESOURCE_ALIAS mail.qml)
qt_add_qml_module(application
    URI ui
    NO_PLUGIN
    VERSION 1.0
    QML_FILES
        main.qml
)
target_link_libraries(application PUBLIC Qt6::Gui Qt6::Quick Qt6::Core)
