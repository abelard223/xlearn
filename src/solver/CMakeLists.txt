# Build library solver
add_library(solver solver.cc checker.cc)

# Build xlearn exe
set(LIBS solver base data loss reader score updater)

add_executable(xlearn main.cc)
target_link_libraries(xlearn ${LIBS})

# Build uinttests
add_executable(solver_test solver_test.cc)
target_link_libraries(solver_test gtest_main ${LIBS})

# Install library and header files
install(TARGETS solver DESTINATION lib/solver)
FILE(GLOB HEADER_FILES "${CMAKE_CURRENT_SOURCE_DIR}/*.h")
install(FILES ${HEADER_FILES} DESTINATION include/solver)