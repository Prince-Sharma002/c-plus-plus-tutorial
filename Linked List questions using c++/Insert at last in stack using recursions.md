# Insert element at last in Stack

```c++

bool isValidParenthesis(string expression)
{
  
    stack<int> solve( stack<int>& s, int x ){
    
    
    // base condition
    if(s.empty()){
        s.push(x);
        return s;
    }
    
    int num = s.top();
    s.pop();
    solve(  s,  x );
    s.push(num);
    return s;
    
}

stack<int> pushAtBottom(stack<int>& myStack, int x) 
{
    // if stack is empty simply push x 
    if( myStack.empty()  ){
        myStack.push(x);
        return myStack;
    }
    
    
    return solve(myStack , x);
    
}
    
    
}

```