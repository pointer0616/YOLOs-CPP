cmake_minimum_required(VERSION 3.0.0)
project(yolos_cpp)

set(ONNXRUNTIME_DIR "${CMAKE_CURRENT_SOURCE_DIR}/onnxruntime-linux-x64-gpu-1.18.0")

# ONNX Runtime 및 OpenCV 요구사항
find_package(OpenCV REQUIRED)

# YOLOs-CPP 라이브러리 생성
add_library(yolos_cpp INTERFACE)
target_include_directories(yolos_cpp INTERFACE 
    ${CMAKE_CURRENT_SOURCE_DIR}/include
    ${ONNXRUNTIME_DIR}/include
    ${OPENCV_LIBS}
)

# OpenCV 및 ONNX Runtime 라이브러리 링크
target_link_libraries(yolos_cpp INTERFACE
    ${OpenCV_LIBS}
    ${ONNXRUNTIME_DIR}/lib/libonnxruntime.so
)
