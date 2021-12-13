# Uses of Const and & in C++


# Contents
- [`Const` Uses](#const-uses)
    - [Declaration of Variables](Declaration of Variables)
    - [Instead of `#define`](#instead-of-define)
    - [Pointers](#pointer)
    - [Member Functions](#in-member-functions)
    - [Function Return Type](#function-return-type)
  
- [`&` Ueses]()  

## `Const` Uses

### Declaration of Variables
- The famous usage of `const` keyword is using it in declaration of variables. 

- Variables declared using `const` are constant and cannot be modified further in the program.

<pre><code><b>const int i = 25</b>;
i = 20;             // try to reassign it <em>(will give error)</em> 
i++;                // try to increment it <em>(will also give an error)</em> 
</code></pre>


### Instead of `#define`
- `const` be used instead of define to define constant values.

- Values defined as const are type-checked and can be used in place of constant expressions.

<pre><code>const int myNewVar = 255;</code></pre>


### Pointer
- It can be used with pointers to:
  
  1. Make the address the pointer pointing to constant 
  <pre><code>const myVar = 10;
  const int* myPointer = &myVar;</code></pre>
  2. Make the pointer constant
  <pre><code>const char *myConstantPtr;</code></pre>
  3. Use `const` pointer to point to `const` variable
  <pre><code>const int const* myConstantPtr;</code></pre>

### In Member functions
- A const member function declaration indicates that the function is a read-only function that does not
  modify the object on which it is called. Persistent member functions cannot modify non-static data members
  or call non-persistent member functions.

  <pre><code>class Date {
  public:
  Date( int mn, int dy, int yr );
  int getMonth() const;     // A read-only function
  void setMonth( int mn );   // A write function; can't be const
  private:
  int month;
  };
  
  int Date::getMonth() const
  {
  return month;        // Doesn't modify anything
  }
  void Date::setMonth( int mn )
  {
  month = mn;          // Modifies data member
  }
  int main()
  {
  Date MyDate( 7, 4, 1998 );
  const Date BirthDate( 1, 18, 1953 );
  MyDate.setMonth( 4 );    // Okay
  BirthDate.getMonth();    // Okay
  BirthDate.setMonth( 4 ); // C2662 Error
  }
  </code></pre>


### Function Return Type
- Putting `const` before the return type of the function, makes it return a constant
  <pre><code>const int constIntFun(){
    return 217;
  }
  </code></pre>

## `&` Uses
