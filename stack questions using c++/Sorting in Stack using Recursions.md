# Sorting in Stack using Recursions

```c++

void sortPush(int num , stack<int> &stack){
    
    
    // !stack.empty() check if stack is not empty by using this if stack is empty
    // then you avoid getting error if you try to access top element of stack
    
    // if num is greater than top element , num will push
    if(  ( !stack.empty() && num > stack.top() )  ||  stack.empty() ){
        
        stack.push(num);
        return ;
        
    }
    
    
    // storing pop element in recursive stack
    int x = stack.top();
    stack.pop();
    
    // recursive call 
    sortPush(num , stack);
    
    
    // inserting pop element 
    stack.push(x);
    

    
}

void sortStack(stack<int> &stack)
{
    // base condition
	if(stack.empty()){
        return ;
    }
    
    
    int num = stack.top();
    stack.pop();
    
    // recursive call until stack is empty
    sortStack(stack);
    
    
    // inserting element in sorted order
    sortPush(num , stack);

}

```