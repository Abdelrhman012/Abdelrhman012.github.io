# <span style="color:Red">Const Usage</span>
### 1) Constant Variables in C++
if you make any variable as **constant**, using const keyword, you cannot change its value. Also, the constant variables must be initialized while they are declared.
```C++
int main
{
    const int i = 10;
    const int j = i + 10;     // works fine
    i++;    // this leads to Compile time error   
}
```
---
### 2) Pointers with const
Pointers can be declared using **const** keyword too. When we use **const** with pointers, we can do it in two ways, either we can apply **const** to what the pointer is pointing to, or we can make the pointer itself a constant.
#### <span style="color:Brown">Pointer to a Const variable</span>
 This means that the pointer is pointing to a **const** variable.
 ```C++
const int* u;
 ```
 Here, u is a pointer that can point to a **const** int type variable. We can also write it like,
 ```C++
 char const* v;
 ```
 still it has the same meaning. In this case also, v is a pointer to an char which is of **const** type.
#### <span style="color:Brown">Const Pointer</span>
To make a pointer **constant**, we have to put the const keyword to the right of the <span style="color:Brown">*</span>.
```C++
int x = 1;
int* const w = &x;
```
Here, w is a pointer, which is const, that points to an int. Now we can't change the pointer, which means it will always point to the variable x but can change the value that it points to, by changing the value of x.

The constant pointer to a variable is useful where you want a storage that can be changed in value but not moved in memory. Because the pointer will always point to the same memory location, because it is defined with const keyword, but the value at that memory location can be changed.

**NOTE:** We can also have a const pointer pointing to a const variable
```C++
const int* const x;
```
---
### 3) const Function Arguments and Return types
We can make the return type or arguments of a function as **const**. Then we cannot change any of them.
```c++
void f(const int i)
{
    i++;    // error
}

const int g()
{
    return 1;
}
```
---
### 4) Defining Class Data members as const
These are data variables in class which are defined using **const** keyword. They are not initialized during declaration. Their initialization is done in the constructor.
```c++
class Test
{
    const int i;
    public:
    Test(int x):i(x)
    {
        cout << "\ni value set: " << i;
    }
};

int main()
{
    Test t(10);
    Test s(20);
}
```
---
### 5) Defining Class Object as const
When an object is declared or created using the **const** keyword, its data members can never be changed, during the object's lifetime.
```c++
const class_name object;
```
For example, if in the class Test defined above, we want to define a **constant** object, we can do it like:
```c++
const Test r(30);
```
---
### 6) Defining Class's Member function as const
A **const** member functions never modifies data members in an object.
```c++
return_type function_name() const;
```
---
# <span style="color:Red">address operator (&) Usage</span>
### 1) Address of static member
The following code fragment shows how the **address-of operator** result differs, depending on whether a class member is static:
```c++
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```
---
### 2) Address of a reference type
Applying the **address-of operator** to a reference type gives the same result as applying the operator to the object to which the reference is bound. For example:
```c++
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```
**output:**
```c++
&d equals &rd
```
---
### 3) Function address as parameter
The following example uses the **address-of operator** to pass a pointer argument to a function:
```c++
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```
**output:**
```c++
25
```