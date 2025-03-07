---
marp: true
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
  }
paginate: true
---

## **C++ concepts and Geant4 Overview**

Deepak Samuel
Central University of Karnataka
<!-- 
```NEUS 2024``` -->

---
## **Geant4**

- A C++ toolkit to simulate particle interactions with matter
- Applications: high energy, nuclear and accelerator physics, as well as studies in medical and space science.

- **Toolkit:** You use it build your own framework - garbage in - garbage out

- Takes sometime to understand, especially for beginners in C++.

- Bonus of learning Geant4: improvement in C++ skills

---
## **Typical pattern of running a c++ code**  

- ``1. Write`` your expressions (code) in C++ in a file (```example.cpp```)
    ```c 
         int a=10;
         int b=10;
         cout<<"The sum is "<<a+b<<endl;
    ```
- ``2. Compile``: convert the above expression to binary format
  -  ```g++ example.cpp -o a```

- ```3. Execute```:
  - ```./a.out```  

    ```c
    The sum is 20
    ```



---
## **Typical pattern of running a c++ code (complex software)**  

- ``1. Write`` 
- ```2. Build```
  - Tells compiler which files to compile, in which order, where they are and location of other required libraries
  - ```cmake```
  - The above command creates a file called ```Makefile```
- ``3. Compile``: 
  -  ```g++ example.cpp -o a``` is replaced by  
  - ```make``` uses Makefile to run the compiler

- ```4. Execute```: ```./a.out```  
---
## **What is a C++ library**

- A set of pre-written code for a specific purpose, usually to be used by others to extend it for their use
- Math library: 
  - Contains code to calculate sin, cos, exp, pi etc...
- Geant4 libraries:
  - Contain code to propagate particles through materials
  - You extend it for your own purposes



---

# **Datatypes in C++**

| **Datatype**    | example            |
|------------|--------------|
| **int**  | 8         |
| **float**  | 8.32         |
| **double** | 8.3457687686 |
| **bool**   | 0/1          |
| **void**   | ?            |
---

# **Class in C++**

- A class is a user defined datatype with its own  data members and member functions or methods.
- Example: 2 x 2 Matrix class: 
    - 4 data members
    - functions or methods to find determinant

 ```c
    class Matrix{
        int a00; // data members
        int a01;
        int a10;
        int a11;

        float determinant(){
            return a00*a11 - a10*a01; // method or a function
        }
    };
```
---

# **File and folder structure**

***Header file (Matrix.h or Matrix.hh files)***
 ```c
    class Matrix{
        int a00; // data members
        int a01;
        int a10;
        int a11;
        float determinant(); // function declaration
    };
```

***Source file (Matrix.cxx or Matrix.cpp files)***

 ```c
 float Matrix::determinant() // function definition
 {
      return a00*a11 - a10*a01; // method or a function
 }
```

- data members have no brackets `()` whereas functions do 

---


# **Geant4 on Github:**

- All header files inside include folder
- All source files inside src folder

> https://github.com/Geant4/geant4/tree/master/examples/basic/B1

> https://github.com/Geant4/geant4/blob/master/examples/basic/B1/include/DetectorConstruction.hh

> https://github.com/Geant4/geant4/blob/master/source/run/include/G4VUserDetectorConstruction.hh


---


# **C++ objects and pointers**

The Matrix class only defines the data members and functions. In order to use it, you have to either

- Create an object: 
    - ```Matrix m```
    - Now, m is called as object of class Matrix

- or Create an pointer to an object:
    - ```Matrix *m = new Matrix()```
    - Now m is the pointer to an object of class Matrix.

- `Quiz` 

---
# **Accessing functions or methods using objects and pointers**

Once an object or pointer is created, you can access the members of the class: 

- Using the object: 
    - ```Matrix m```
    - m.determinant()

- or using the pointer to an object:
    - ```Matrix *m = new Matrix()```
    - m->determinant();

- The dot operator is used on object while the arrow operator is used on pointers.

---

# **Constructors and destructors**

```c 
Matrix m
m.determinant()
```

```c
Matrix *m = new Matrix()
m->determinant();
```
After the above two lines, what would be the value of the determinant? 

---
# **Constructors**

- The determinant is undefined since the values of the matrix elements are not set!

- **Constructor:** special function automatically called when an object or its pointer is created. Can be used to initialize the values of certain data members or any similar action. 

- Constructor has the same name as that of the class!

 ```c
    class Matrix{
        Matrix(int a1, int a2, int a3, int a4) {a00=a; a01=a2; a10=a3; a11=a4;}       
        int a00; // data members
        int a01;
        int a10;
        int a11;
        float determinant(); // function declaration
    };
    
    Matrix m(1,1,1,1) // or  Matrix *m = new Matrix(1,1,1,1);
   
```
---
# **Destructors**
- When too many pointers are created, there could be memory issues. Care should be taken to delete the pointers as soon as they are not required. A destructor is a special function that is called when an pointer is deleted. 
- **Destructor** has the same name as the class with a ~ in front

 ```c
    class Matrix{
        Matrix(int a1, int a2, int a3, int a4) {a00=a; a01=a2; a10=a3; 
        a11=a4;} // constructor
        ~Matrix(); // destructor      
        int a00; // data members
        int a01;
        int a10;
        int a11;
        float determinant(); // function declaration
    };
    
    Matrix *m = new Matrix(1,1,1,1);
    delete m;
   
```
---
# **Inheritance**
- A new class can be created based on an existing class, utilizing the members and functions of the original class. This is called class inheritance

 ```c
    class PauliSpinXMatrix:Public Matrix{
        // your functions here

    };
      
```
**Matrix** is the parent or base class and **PauliSpinMatrix** is the inherited class.

---
# **Abstract Class**

- An abstract class is a class that is designed to be specifically used as a base class. 
- An abstract class contains at least one pure virtual function. 
```c 
class Matrix {
public:
  virtual void f() = 0;
};
```
- you cannot directly declare an object or pointer of an abstract class