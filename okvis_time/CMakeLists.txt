cmake_minimum_required(VERSION 2.8.11)

project(okvis_time)

if(libvisensor_FOUND)
  add_definitions(-DHAVE_LIBVISENSOR)
  message(STATUS "Found libvisensor. Setting HAVE_LIBVISENSOR flag.")
endif()

# build the library
add_library(${PROJECT_NAME} src/Time.cpp src/Duration.cpp)

# installation if required
install(
  TARGETS ${PROJECT_NAME}
  EXPORT okvisTargets
  ARCHIVE DESTINATION "${INSTALL_LIB_DIR}" COMPONENT lib)
install(
  DIRECTORY include/
  DESTINATION ${INSTALL_INCLUDE_DIR}
  COMPONENT dev
  FILES_MATCHING
  PATTERN "*.hpp")
