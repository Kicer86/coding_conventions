
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

* Do not place argument name in header file when argument type clearly defines its purpose. Example: <br/>
  void setPath(const std::string &);<br/>
  void setWidth(int pixels);   // setWidth(int) could be not enought<br/>
  void setData(const Date &);<br/>
  void ClassConstructor(const Time& startTime, const Time& endTime); // meaning of arguments in constructor may be not clear<br/>

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

### Memory management
* Do not use **new** nor **delete** keywords. Use std::make_unique or std::make_shared instead. This helps memory management:
  - object's ownership can be passed only with std::unique_ptr move which is clear and obvious. 
  - **delete** will be never called on invalid memory (like stack object passed as raw pointer).
  
* When it is necessary to pass **std::unique_ptr**'s content use raw pointer (**std::unique_ptr::get()**). There is no need to pass whole **std::unique_ptr** as reference.

### C++ features
* Do not use RTTI. When you need it there must be something wrong. Exception from this rule is to use **dynamic_cast<>** in **assert**s.
* Do not use exceptions. <br/>
  - when new **throw** is added to the function it is necessary for the developer to analyze all its callers if there is proper **try**-**catch** sequence.
  - it is necessary to remember about possible exceptions when writing code. Each used function may **throw**.

### Macros
* Macros should be used only as include guard. Do not use it for other reasons as long as your goal can be achieved with c++ (templates for examples).
* Name macros with BIG_LETTERS_AND_UNDERSCORES.

### Coding tips
* Consider using **std::function** instead of tiny interfaces in classes which emit notifications. <br/>
  This reduces number of small classes and multiple inheritance situations. It is also more flexible solution as clients can provide free functions and are not forced to use particular function names.
