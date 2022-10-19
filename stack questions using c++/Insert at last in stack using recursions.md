# Insert element at last in Stack

```c++


stack<int> pushAtBottom(stack<int>& myStack, int x) 
{
    // if stack is empty simply push x 
    if( myStack.empty()  ){
        myStack.push(x);
        return myStack;
    }
    
    
    return solve(myStack , x);
    
}
    
    


```
