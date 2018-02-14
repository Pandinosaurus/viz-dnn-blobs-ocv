cmake_minimum_required(VERSION 2.8)
project( visualizeDnnBlobsOCV )

find_package( OpenCV )
include_directories( ${OpenCV_INCLUDE_DIRS} )
link_directories(  ${OpenCV_INCLUDE_DIRS} )
SET(CMAKE_CXX_FLAGS "-std=c++11")

add_executable( visualizeDnnBlobsOCV
		src/main.cpp )

target_link_libraries( visualizeDnnBlobsOCV
			${OpenCV_LIBS} )

#You may need to change the change the "${OpenCV_DIR}/bin/Debug/" to your installation path
add_custom_command(TARGET visualizeDnnBlobsOCV POST_BUILD
COMMAND ${CMAKE_COMMAND} -E copy_directory
D:/opencv/build/bin/Debug
"$<TARGET_FILE_DIR:visualizeDnnBlobsOCV>"
)

#You may need to change the change the "${OpenCV_DIR}/bin/Release/" to your installation path
add_custom_command(TARGET visualizeDnnBlobsOCV POST_BUILD
COMMAND ${CMAKE_COMMAND} -E copy_directory
D:/opencv/build/bin/Release
"$<TARGET_FILE_DIR:visualizeDnnBlobsOCV>"
)