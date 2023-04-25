cmake_minimum_required(VERSION 3.0)

project(RAMSSAHG)

add_definitions(-DUNICODE -D_UNICODE)

set(CMAKE_SYSTEM_VERSION 10.0)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_WIN32_EXECUTABLE  ON)

file(GLOB SOURCES "src/*.cpp")
file(GLOB_RECURSE HEADERS include/*.h)

source_group("Headers" FILES ${HEADERS})

set(KINECTSDK20_DIR "C:/Program Files/Microsoft SDKs/Kinect/v2.0_1409")
include_directories(${KINECTSDK20_DIR}/inc include)
link_directories(${KINECTSDK20_DIR}/Lib/x64)

add_executable(${PROJECT_NAME} WIN32 ${HEADERS} ${SOURCES})

target_link_libraries(
    ${PROJECT_NAME} 
    kinect20.lib
    kernel32.lib
    user32.lib
    gdi32.lib
    winspool.lib
    comdlg32.lib
    advapi32.lib
    shell32.lib
    ole32.lib
    oleaut32.lib
    uuid.lib
    odbc32.lib
    odbccp32.lib
)
