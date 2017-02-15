cmake_minimum_required(VERSION 3.1)

project(label_image)

cmake_policy(SET CMP0022 NEW)

if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
  set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} "-fno-exceptions -std=c++11")
endif()

set(tf_label_image_example_srcs
  "${CMAKE_SOURCE_DIR}/main.cc"
)

include_directories(${CMAKE_SOURCE_DIR}/../../..)
# include_directories(${CMAKE_SOURCE_DIR}/../../../third_party/eigen3)
# include_directories(/home/developer/data/prj/tensorflow/tensorflow/contrib/cmake/eigen/src)
include_directories(/home/developer/data/prj/tensorflow/tensorflow/contrib/cmake/build/eigen/src/eigen)
include_directories(/home/developer/data/prj/tensorflow/tensorflow/contrib/cmake/build)
link_directories(/home/developer/data/prj/tensorflow/tensorflow/contrib/cmake/build)
link_directories(/home/developer/data/prj/tensorflow/tensorflow/contrib/cmake/build/zlib/install/lib)
link_directories(/home/developer/data/prj/tensorflow/tensorflow/contrib/cmake/build/gif/install/lib)
link_directories(/home/developer/data/prj/tensorflow/tensorflow/contrib/cmake/build/png/install/lib)

add_executable(tf_label_image_example
  ${tf_label_image_example_srcs}
)

target_link_libraries(tf_label_image_example PUBLIC
  z
  gif
  tf_protos_cc
)
