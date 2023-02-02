# Class in C++

Hey, guys today I am talking about Classes in C++, I hope you will learn something new from this article. Let us begin.

Before you start object-oriented programming, you should learn the basics of C++ so you will be comfortable with the code. You can refer to my article, to get an idea of a c++ program [click Here](https://jyotirmoy.hashnode.dev/basic-c-syntax-for-beginners).

If you are learning OOPs then the first thing you will learn is Class, Class is an important part of c++.

# Class

In Class, we can have data members and member functions, and it is user-defined. In simple words, we can have different functions and data types inside a function and even we can hide data from other programs. 

A class can be made using a **class** keyword followed by the name of the class. The code should be written inside a {} bracket and closed using a semicolon **;** at the end.
```
class classname{
        access specifier:   // Access specifier can be private or public
        data member;        // data member can be int, char, string, double
        member function(){} // member function is a function inside a class
};
```
Now, let us see three things:
- Access Specifier
- Data Member
- Member function

## Access Specifier
Access specifier defines a data member or a member function should be private or public, by default a class is set to private which means we can't access anything without a public keyword.

Let us see an example :
```
class test{
        int a;
};
```
By default, we can't access integer **a** as this is private, but even if it is private we can access it in a public member function. First, we need to add a **public:** keyword after which whatever we will write will be public.
```
class test{
        int a;
        public:
            void printNumber(){
                  cout<<a<<endl;
            }
};
```
As you can see in the printNumber() function we can access the integer **a** and print it in the terminal, but we did not initialize any value in **a** so it will return a garbage value.
>Garbage value is a value that the computer gives automatically.

## Data Member
Now let us see the data member, data members are the data types or variables inside a class in which the value are stored.
```
class test{
      int num;
      char character;
      double numdouble;
      string word;

      public:
};
```
Here, we can see the variable of different data types which is inside a class and all these variables are private but we can make a data member public, we just need to write the data member after the public keyword but we should keep the data member inside the private specifier.

## Member Function
We can write the functions inside the class which can access the data member inside the private which helps us to insert the value and we can use the member function as a normal function.
```
class test{
        int number;
        public:
            // function to insert a value inside a number
            void setNumber(int num){
                 number=num;
             }
             // Function to print out the number value
             void printNumber(){
                 cout<<number<<endl;
             }
};
```
We can even write a function outside of the class just we need to declare the function inside the class.
```
class test{
        int number;
        public:
            // function to insert a value inside a number
            void setNumber(int num){
                 number=num;
             }
             // we just declared a function inside a class
             void printNumber();
};
void test::printNumber(){
        cout<<number<<endl;
}
```
<hr>
# Declaration of Object
Till now we have seen how to make a class, and now we will use make an object. The syntax of the class starts with the class name and after that object name end with a semicolon.

Before the Declaration no memory or storage is allocated, it is allocated after the object declaration.
```
classname objectname;
```
```
include<iostream>
using namespace std;

class test{
        int number;
        public:
            // function to insert a value inside a number
            void setNumber(int num){
                 number=num;
             }
             // Function to print out the number value
             void printNumber(){
                 cout<<number<<endl;
             }
};

int main(){
        test test1;  // Declaration of an object
        return 0;
}
```
# Accessing Data Member and Member Function
We can access the Member function and Data Member by Object Name followed by a dot '.' and the Data Member or Member function.
```
include<iostream>
using namespace std;

class test{
        int number;
        public:
            // function to insert a value inside a number
            void setNumber(int num){
                 number=num;
             }
             // Function to print out the number value
             void printNumber(){
                 cout<<number<<endl;
             }
};

int main(){
        test test1;  // Declaration of an object
        
        // NEW Lines
        test1.setNumber(1);  //This line call the setNumber function
        test1.printNumber;  //This line is calling the printNumber function

        return 0;
}
```
As you can see two new lines have been added, the first line which will call the **setNumber ** function which will set the value of the number variable as we have passed which is 1. After the number variable value is set, the second line will call the second function (**printFunciton**) which is just to print the value of the number variable.

Output
```
1
```
<hr>
# Constructor
A Constructor is a type of function that will only run once and at the time of object declaration. It is helpful when we need to set data member values. A Constructor does not return any data, so we do not need to give any type of data type in front of the constructor name.

A Constructor name should be the same as the class name. There are three types of constructors:
- Default Constructor
- Parameterized Constructor
- Copy Constructor

## Default Constructor
Default Constructor runs when no parameter is given.
```
#include<iostream>
using namespace std;

class test{
        int a;
        public:
            // Creating a Default Constructor
            test(){
                a=0;  // By default it will set the value of a to 0
                       // instead of any garbage value
            }
            void aPrint(){
                cout<<a<<endl;
            }
};
```
```
0  //output
```
Without a constructor will return a garbage value like 63633738 or 87262828.

## Parameterized Constructor
Parameterized Constructor runs when we provide some parameter.

>If you make Parameterized Constructor, It is necessary to make a default constructor. 

```
#include<iostream>
using namespace std;

class test{
        int a;
        public:
            // Creating a Default Constructor
            test(){
                a=0;  // By default it will set the value of a to 0
                       // instead of any garbage value
            }
            // Creating a Parameterized Constructor
            test(int numa){
                a=numa;
            }
            // Function to print the value if 'a' variable
            void aPrint(){
                cout<<a<<endl;
            }
};

int main(){
        test test1(1); // Creating a Object with Parameter
        test1.aPrint();
        return 0;
}
```
```
1 // Output
```

## Copy Constructor
The copy constructor is used when we need to make a copy of the premade object.
```
#include<iostream>
using namespace std;

class test{
        int a;
        public:
            // Creating a Default Constructor
            test(){
                a=0;  // By default it will set the value of a to 0
                       // instead of any garbage value
            }
            
            // Creating a Parameterized Constructor
            test(int numa){
                a=numa;
            }
            // Creating a Copy constructor
            test(test &oj){
                a=oj.a;
            }
            // Function to print the value if 'a' variable
            void aPrint(){
                cout<<a<<endl;
            }
};

int main(){
        test test1, test2(1); // Creating a Object with Parameter
        test test3(test2); // Coping test2 into test3
        test1.aPrint();
        test2.aPrint();
        test3.aPrint();
        return 0;
}
```
```
// Output
0  // Value is 0 Because of default constructor
1  // Value is 1 Because of the parameter constructor
1  // Value is 1 Because of the copy constructor
```

# Example
- Add two number
- Subtract two number
- Calculator
- Area of Circle

## Add two number
```
#include<iostream>
using namespace std;

class add{
    int num1;
    int num2;

    public:
    int add_(int n1,int n2){
        num1=n1;
        num2=n2;
        return num1+num2;
    }
    
};

int main(){
    int a,b;
    cout<<"Enter your first number: ";
    cin>>a;
    cout<<"Enter your second number: ";
    cin>>b;
    class add add1;
    cout<<"Answer: "<<add1.add_(a,b)<<endl;
    return 0;
}
```

## Subtract two number
```
#include<iostream>
using namespace std;

class sub{
    int num1;
    int num2;

    public:
    int sub_(int n1,int n2){
        num1=n1;
        num2=n2;
        return num1-num2;
    }
    
};

int main(){
    int a,b;
    cout<<"Enter your first number: ";
    cin>>a;
    cout<<"Enter your second number: ";
    cin>>b;
    class sub sub1;
    cout<<"Answer: "<<sub1.sub_(a,b)<<endl;
    return 0;
}
```
## Calculator
```
#include<iostream>
using namespace std;

class cal{
    int num1;
    int num2;

    public:
    cal(){
        num1=0;
        num2=0;
     }
    int add(int n1,int n2){
        num1=n1;
        num2=n2;
        return num1+num2;
    }
    int sub(int n1,int n2){
        num1=n1;
        num2=n2;
        return num1-num2;
    }
    int div(int n1,int n2){
        num1=n1;
        num2=n2;
        return num1/num2;
    }
    int mul(int n1,int n2){
        num1=n1;
        num2=n2;
        return num1*num2;
    }
    int rem(int n1,int n2){
        num1=n1;
        num2=n2;
        return num1%num2;
    }
    
};

int main(){
    int a,b;
    cout<<"Enter your first number: ";
    cin>>a;
    cout<<"Enter your second number: ";
    cin>>b;
    class cal num1 ;
    cout<<num1.add(a,b)<<endl;
    cout<<num1.sub(a,b)<<endl;
    cout<<num1.div(a,b)<<endl;
    cout<<num1.mul(a,b)<<endl;
    cout<<num1.rem(a,b)<<endl;
    return 0;
}
```
## Area of Circle
```
#include<iostream>
using namespace std;

class circle{
        double pi=3.1416;
        int radius;
    public:
        double getarea(int r){
            radius=r;
            double area=pi*radius*radius;
            return area;
        }
};

int main(){
    cout<<"Enter the radius of circle : ";
    int radius;
    cin>>radius;
    class circle c;
    cout<<"Area of Circle for "<<radius<<" is "<<c.getarea(radius)<<endl;
    return 0;
}
```