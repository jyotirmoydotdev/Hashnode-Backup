# Basic C++ Syntax for Beginners

# Introduction to a simple C++ file
>This C++ file will do Nothing

Today we are seeing the basic syntax of C++, if you can learn c++ it will be helpful for you in learning other programming languages such as **Javascript**, **C**, and **Java**.
```
#inlcude<iostream>
``` 
Every C++ program starts with a header file. `#include<iostream>` mean to add the standard input-output stream. This header helps us to get input and display output in the terminal.
```
using namespace std;
``` 
Second-line which is `using namespace std;` I prefer to write this line as it makes it easier to write the C++ code for beginners, but in the industry, it is considered bad to use it.
```
int main(){
    // Write your code here
    return 0;
}
``` 
This is the main place where you will be writing the code for your program (after the comment ).

> If you are thinking about what is `comment`, the sentence which says `// Write your code here` anything written after `//` is ignored by the program. we will be reading it later on in this article.


```
#include<iostream>
using namespace std;

int main(){
    // Write your code here;
    return 0;
}
```
So, after writing the code together the code seemed like this. 
After each line we need to put `;` this means the line has been ended;
<hr>

# Program to print Hello World!

```
#include<iostream>
using namespace std;

int main(){
    cout<<"Hello, World!"<<endl;
    return 0;
}
``` 

```
// Output
Hello, world!
``` 

Here you can see two new words one is `cout` and another one is `endl` let me explain what it is.

These two are reserve keywords and even **include, int, main, return, and using** are reserve keywords that mean something the compiler understands.

`cout` is used to display any data in the terminal and

`endl` is used to print a new line, by default c++ does don't print a new line on its own it will print a `%` sign at the end.
<hr>

# Contact
Do follow me on Twitter [@jyotirmoydotdev](https://twitter.com/jyotirmoydotdev)
