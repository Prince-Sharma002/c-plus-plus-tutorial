
# POINTER IN C++

studying pointer is really fun

simple defintion - pointer is a special variable that have a ability to store only address. 

lets grab some basic information first

## How normal variable store data

- Normal variable name is only a address using which we can find the data in memory . 
- The address is map with variable name in [symbol table](https://www.geeksforgeeks.org/symbol-table-compiler/).
- Whenever variable is use , the compiler use the address map with variable store in symbol table.
- The address store is in [Hexadecimal form](https://en.wikipedia.org/wiki/Hexadecimal)  .
- To get this address of variable you can use " &variable_name ".


```c++
//first initialize a variable name "num" that can store integer
int num  = 10;

// To get the address use "&" we generally call it  "address operator" 
cout<< "the address is " << &num;

```

##  What is Pointer ?

- Pointer is a variable that can store the address of another variable .

```c++
// syntax of creating a pointer 
int num = 10;
int *p = &num;
```
- In this case we specify the datatype int of pointer because the address that pointer store is pointing to integer .
- You can observe pointer name "p" store address of num .
## Dereference Pointer ( How to use pointer )

 Dereference pointer gives value of that address pointing to .

```c++
//dereferecing pointer
cout<<"the value that address point to can get by pointer is " << *p;
//output - 10
```

## Address store by pointer


```c++
cout<< "address store by pointer p is " << p <<endl;
cout<< "address map with num variable is " << &num << endl;
```
you can find both address are equal .


## Create an Empty pointer

```c++
//Creating an empty pointer
int* p;
```

- It is bad practice to declare an empty pointer ( Do google ) .
- Avoid dereferencing an empty pointer .


## Update using Pointer

```c++
int num = 10;
    
int* p = &num;

//update num value using pointer
*p = 15;

cout << "value of updated num is " << num;

```


## How `*` meaning changes ?

- `*` is use while declaring a pointer . 
- After declaration of pointer the only meaning of `*` is , it is use for dereferencing ( to access the value a pointer point to ). 















## Appendix

For question practice - https://www.codingninjas.com/codestudio/guided-paths/pointers
