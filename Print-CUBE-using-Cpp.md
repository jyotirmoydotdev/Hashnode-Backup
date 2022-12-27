# Print CUBE using C++

```
#include<iostream>
using namespace std;

int main(){
    int n;
    cout<<"Enter the rows for Cube: ";
    cin>>n;
    for (int i=0;i<n;i++){
        for (int j=0;j<n;j++){
            cout<<"* ";
        }
        cout<<endl;
    }
    return 0;
}
``` 
**Output**
```
Enter the rows for Cube: 4

* * * *
* * * *
* * * *
* * * *
``` 

**Code 2**
```
#include<iostream>
using namespace std;

int main(){
    int n;
    cout<<"Enter the rows for Cube: ";
    cin>>n;
    Cout<<"Enter the symbol or character: ";
    string x;
    cin>>x;
    for (int i=0;i<n;i++){
        for (int j=0;j<n;j++){
            cout<<x<<" ";
        }
        cout<<endl;
    }
    return 0;
}
``` 
**Output**
```
Enter the rows for Cube: 4
Enter the symbol or character: $

$ $ $ $
$ $ $ $
$ $ $ $
$ $ $ $
```
## Explanation

When *i=0*  *j* will be running **n** times for each time *j* runs it will print ***** and after *j* has completed **n** number of times it will print a new line after that *i=1* and again *j* will run **n** times this process will continue till *i* runs n number of times.

You can visit my [cpp-language](https://github.com/jyotirmoydotdev/Cpp-Language) repo in github to see all the c++ program which I have written.

And do follow me on Github [@jyotirmoydotdev](https://github.com/jyotirmoydotdev/)