
### General rules ###

* Keep CMake files simple. Do not complicate more than necessary. Most functionality is already provided by CMake.
* Do not modify compiler flags via CMAKE_CXX_FLAGS (and similar) variables. these flags should be modified by user only. 
  If adding compiler flag is necessary use COMPILE_FLAGS property for source file/target.
