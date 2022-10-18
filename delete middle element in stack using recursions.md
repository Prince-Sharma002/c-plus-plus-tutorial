# Delete Middle Element in Stack using Recursions

```c++

void DeleteElement(stack<int>&inputStack , int count , int n){
    
    // base condition
    if(count  == n/2){
        inputStack.pop();
        return ;
    }
    
    int num = inputStack.top();
    inputStack.pop();
    count++;
    DeleteElement(inputStack , count , n);
    
    inputStack.push(num);
    
    
}


void deleteMiddle(stack<int>&inputStack, int N){
	
   
    int count = 0; 
    DeleteElement(inputStack , count , N);
   
}

```