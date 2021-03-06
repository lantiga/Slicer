
#-----------------------------------------------------------------------------
set(CLP ${MODULE_NAME})

#-----------------------------------------------------------------------------
add_executable(${CLP}Test ${CLP}Test.cxx)
target_link_libraries(${CLP}Test  ${CLP}Lib)
set_target_properties(${CLP}Test PROPERTIES LABELS ${CLP})

# configure the input mrml file to copy it to the binary TEMP dir so
# the test doesn't modify the source tree one
configure_file(
  ${TEST_DATA}/ACPCTest.mrml
  ${TEMP}/ACPCTest.mrml
  COPYONLY
  )

set(testname ${CLP}Test)
add_test(NAME ${testname} COMMAND ${Launcher_Command} $<TARGET_FILE:${CLP}Test>
  ModuleEntryPoint
#  --acpc ${TEST_DATA}/ACPC.fcsv --midline ${TEST_DATA}/midsag.fcsv
  --acpc 0.5,-21.5,-9.5 --acpc -2.5,4.5,-16.5 --midline 12.5,-93.5,7.5 --midline 12.5,-93.5,-12.5 --midline 5.5,-93.5,-25.5 --midline 9.5,-83.5,-22.5 --midline 9.5,-83.5,-12.5 --midline 10.5,-83.5,10.5 --midline 10.5,-83.5,26.5 --midline 7.5,-68.5,38.5 --midline 7.5,-68.5,13.5 --midline 6.5,-68.5,-9.5 --midline 5.5,-68.5,-30.5 --midline 5.5,-68.5,-48.5 --midline 3.5,-49.5,50.5 --midline 4.5,-49.5,25.5 --midline 3.5,-49.5,5.5 --midline 4.5,-49.5,-32.5 --midline 3.5,-34.5,54.5 --midline 1.5,-34.5,30.5 --midline 1.5,-34.5,17.5 --midline 3.5,-34.5,-22.5 --midline 1.5,-19.5,58.5 --midline 0.5,-19.5,34.5 --midline 0.5,-19.5,18.5 --midline 0.5,-19.5,-13.5 --midline 1.5,-19.5,-25.5 --midline -1.5,-4.5,62.5 --midline -2.5,-4.5,36.5 --midline -1.5,-4.5,19.5 --midline -1.5,-4.5,0.5 --midline -1.5,-4.5,-12.5 --midline -1.5,-4.5,-24.5 --midline -1.5,-4.5,-39.5 --midline -3.5,10.5,49.5 --midline -1.5,10.5,28.5 --midline -3.5,10.5,14.5 --midline -2.5,10.5,5.5 --midline -3.5,10.5,-15.5 --midline -1.5,10.5,-33.5 --midline -5.5,26.5,44.5 --midline -6.5,26.5,25.5 --midline -5.5,26.5,3.5 --midline -5.5,26.5,-11.5 --midline -5.5,26.5,-21.5 --midline -5.5,26.5,-35.5 --midline -5.5,41.5,35.5 --midline -7.5,41.5,12.5 --midline -6.5,41.5,-4.5 --midline -7.5,41.5,-27.5 --midline -7.5,41.5,-41.5 --midline -7.5,56.5,24.5 --midline -9.5,56.5,-0.5 --midline -9.5,56.5,-12.5 --midline -9.5,56.5,-29.5 --midline -10.5,71.5,3.5 --midline -10.5,71.5,-12.5 --midline -11.5,71.5,-26.5 --outputTransform ${TEMP}/ACPCTest.mrml\#vtkMRMLLinearTransformNode1
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

