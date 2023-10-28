cmake_minimum_required(VERSION 3.5)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)
cmake_policy(SET CMP0071 NEW)

find_package(Qt6 REQUIRED COMPONENTS Core Gui Quick)
qt_standard_project_setup()
add_library(ui STATIC)
qt_add_qml_module(ui
    URI ui
    NO_PLUGIN   #<-- code ends up in ui and not in static lib uiplugi
    VERSION 1.0
    QML_FILES
        main.qml
)
target_link_libraries(ui PUBLIC Qt6::Gui Qt6::Quick Qt6::Core)
