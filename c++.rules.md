
### Formatting

* No tabs, 4 spaces indention
* Spaces around arithmetic operators. Example: int a __=__ 1 __+__ 2;
 
### Naming
* Type name should start with capital letter and have a capital letter for each new word. 

  Example: Class, ClassName, MyTypeDef
  
  This rule applies to classes, structs, typedefs, enums etc.
  
* Functions and methods should start with lowercase and have capital letter for each new word.

  Example: myGlobalFunction, Class::someMethod

### Source files layout
* Header files should be self-sufficient.
  http://stackoverflow.com/questions/1892043/self-sufficient-header-files-in-c-c

* Header files layout:
  - optional description
  - includes
  - forward declarations
  - definitions and declarations
  
  Each group should be separated with empty line. 
  #include directives should be grouped by library (starting with std, ending with local include files) and each group should be separated with empty line. 
  #include directives should be sorted alphabetically (by file path/name) within each group.

* C/C++ files layout is the same as for header files but related header file should be included as first to be sure it is self-sufficient.
  
