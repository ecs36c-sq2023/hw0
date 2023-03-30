add_library(
    insertion_sort
    insertion_sort.cpp
    utils.hpp
)
# Create a library named `insertion_sort`

target_include_directories(insertion_sort PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
# This command add the include path to the target `insertion_sort`,
# as well as targets that link `insertion_sort`.
