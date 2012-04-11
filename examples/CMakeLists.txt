set( _example
cascade_train
momentums
mushroom
robot
scaling_test
scaling_train
simple_test
simple_train
steepness_train
xor_test
xor_train
)

include_directories( ${FANN_SOURCE_DIR}/src/include )

foreach( var ${_example} )
  configure_file( ${CMAKE_CURRENT_SOURCE_DIR}/${var}.c.in
    ${CMAKE_CURRENT_BINARY_DIR}/${var}.c
    @ONLY
  )
  add_executable( ${var} ${CMAKE_CURRENT_BINARY_DIR}/${var}.c )
  target_link_libraries( ${var} fann m )

  add_test( NAME ${var}_TEST COMMAND ${var} )
endforeach()

configure_file( ${CMAKE_CURRENT_SOURCE_DIR}/xor_sample.cpp.in
  ${CMAKE_CURRENT_BINARY_DIR}/xor_sample.cpp
  @ONLY
  )

add_executable( xor_sample ${CMAKE_CURRENT_BINARY_DIR}/xor_sample.cpp )
target_link_libraries( xor_sample fann m )

add_test( NAME xor_sample_TEST COMMAND xor_sample )
