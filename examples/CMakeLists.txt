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
  add_executable( ${var} ${var}.c )
  target_link_libraries( ${var} fann m )
endforeach()
