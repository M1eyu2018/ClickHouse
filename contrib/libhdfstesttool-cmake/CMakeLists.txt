set(HDFS_TEST_TOOL_ROOT_DIR "${ClickHouse_SOURCE_DIR}/contrib/libhdfstesttool")
set(HDFS_TEST_TOOL_SOURCE_DIR "${HDFS_TEST_TOOL_ROOT_DIR}/src")
set(HDFS_TEST_TOOL_INCLUDE_DIR "${HDFS_TEST_TOOL_ROOT_DIR}/include")

set(
    SRCS
    "${HDFS_TEST_TOOL_SOURCE_DIR}/common/HDFSConfig.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/common/HdfsOperator.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/common/Properties.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/common/SimpleProperties.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/task/CreateTask.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/task/DeleteTask.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/task/DiffTask.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/task/ReadFileTask.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/task/MixTask.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/task/ExcuteTask.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/task/AppendTask.cpp"
    "${HDFS_TEST_TOOL_SOURCE_DIR}/task/ReadSameFileTask.cpp"
)

add_executable(bigo_libhdfs_test ${HDFS_TEST_TOOL_ROOT_DIR}/LibhdfsTest.cpp ${SRCS})

target_include_directories(bigo_libhdfs_test PRIVATE ${HDFS_TEST_TOOL_INCLUDE_DIR})
target_include_directories(bigo_libhdfs_test PRIVATE ${HDFS_TEST_TOOL_INCLUDE_DIR}/common)
target_include_directories(bigo_libhdfs_test PRIVATE ${HDFS_TEST_TOOL_INCLUDE_DIR}/task)
target_include_directories(bigo_libhdfs_test PRIVATE ${HDFS_TEST_TOOL_INCLUDE_DIR}/spdlog)
target_include_directories(bigo_libhdfs_test PRIVATE ${ClickHouse_SOURCE_DIR}/contrib/libhdfs3/include/hdfs)
target_include_directories(bigo_libhdfs_test PRIVATE ${ClickHouse_SOURCE_DIR}/contrib/protobuf/src)

target_link_libraries(bigo_libhdfs_test ch_contrib::hdfs)
target_link_libraries(bigo_libhdfs_test ${ClickHouse_SOURCE_DIR}/contrib/libhdfstesttool-cmake/lib/libspdlog.a)

