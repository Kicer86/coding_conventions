
### Formatting

#### General

* No tabs, 4 spaces indention
* Spaces around arithmetic operators. Example: int a __=__ 1 __+__ 2;

#### Arguments
* Put space between type name and reference (&) or pointer (\*) character when there is no argument name.<br/>
  Example:<br/>
           void foo(bar *); <br/>
           void foo(bar &, foobar *);

* Do not put space between type name and reference (&) or pointer (\*) character when there is argument name
  or this is return type.<br/>
  Example: <br/>
           const int& getInt() const;<br/>
           void setValue(Type& value);<br/>
           void setModel(Model\* model);<br/>
           Model\* getModel();<br/>

### Naming
* Type name should start with capital letter and have a capital letter for each new word. 

  Example: Class, ClassName, MyTypeDef<br/>
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
  \#include directives should be grouped by library (starting with std, ending with local include files) and each group should be separated with empty line. 
  \#include directives should be sorted alphabetically (by file path/name) within each group.

* C/C++ files layout is the same as for header files but related header file should be included as first to be sure it is self-sufficient.
 
### Functions
* Functions should have no more than 2-3 arguments. It increases readability and reduces possible problems with single responsibility.
* Return by value. It is easier to read the code, clients can *const* returned value, RVO and move semantic make it fast as returning by in/out argument. 

### Coding tips
* Consider using **std::function** instead of tiny interfaces in classes which emit notifications. <br/>
  This reduces number of small classes and multiple inheritance situations. It is also more flexible solution as clients can provide free functions and are not forced to use particular function names.
