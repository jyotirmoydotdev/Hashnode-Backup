# Remove Even Integers From an Array

Implement a function `RemoveEven( int *& arr, int n )` which takes an array `arr` and its size and removes all the even elements from a given array.

> **Input**
> 
> ```cpp
> 5
> 1 2 3 4 5
> ```

> **Output**
> 
> ```cpp
> 1 3 5
> ```

# Solution

```cpp
#include<iostream>
using namespace std;
int NewArraySize=0;
int * RemoveEven(int *& arr, int n){
    int * NewArray=new int[]{};
    for (int i=0;i<n;i++){
        if ((arr[i]%2)==1){
            NewArray[NewArraySize++]=arr[i];
        }
    }
    delete [] arr;
    arr=NewArray;
    return arr;
}

int main(){
		// Array size
    int n=0;
		cin>>n;

		// Array
    int * arr=new int[n]{};
		for (int i=0;i<n;i++){
				cin>>arr[i];
		}
		
		// Calling the funciton
    arr = RemoveEven(arr,n);
		
		// Printing the new array
    for (int i=0;i<NewArraySize;i++){
        cout<<arr[i]<<" ";
    }
    cout<<endl;
    return 0;
}
```

Here inside the function `RemoveEven()`we created a new dynamic array `NewArray`which will be used to store the **odd** element. Next, we are using a **for loop** to check if an element in an array of index i is odd or even if the reminder is 1 then it is an odd number, it will be pushed in the `NewArray` and then the variable `NewArraySize` will be + 1 so we can keep track of the size of the array as we can’t get the dynamic array size with `sizeof()` function. After, we have successfully added all the odd number elements in the `NewArray` we will delete all the elements of the `arr` as we want to copy the `NewArray` elements in `arr` and then return it.

> Run the code with `g++ -std=c++20 fileName.cpp -o a.out` and `./a.out`
