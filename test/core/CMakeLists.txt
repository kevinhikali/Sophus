# Ensure that ${Sophus_INCLUDE_DIR} is first on search path
INCLUDE_DIRECTORIES( BEFORE ${Sophus_INCLUDE_DIR} )
INCLUDE_DIRECTORIES( SYSTEM ${EIGEN3_INCLUDE_DIR} )

# Tests to run
SET( TEST_SOURCES test_common test_so2 test_se2 test_rxso2 test_sim2 test_so3 test_se3 test_rxso3 test_sim3 test_velocities test_geometry)

FOREACH(test_src ${TEST_SOURCES})
  ADD_EXECUTABLE( ${test_src} ${test_src}.cpp tests.hpp ../../sophus/test_macros.hpp)
  ADD_TEST( ${test_src} ${test_src} )
ENDFOREACH(test_src)
