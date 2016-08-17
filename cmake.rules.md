
### General rules ###

* Keep CMake files simple. Do not complicate more than necessary. Most functionality is already provided by CMake.
* Do not modify compiler flags via CMAKE_CXX_FLAGS (and similar) variables. these flags should be modified by user only. 
  If adding compiler flag is necessary use COMPILE_FLAGS property for source file/target.<br/>
  Examples:<br/>
  set_source_files_properties(file.cpp PROPERTIES COMPILE_FLAGS ${OpenMP_CXX_FLAGS})<br/>
  target_compile_options(project_name PRIVATE foo bar)
