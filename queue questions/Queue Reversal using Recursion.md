#  Queue Reversal using Recursion

```c++

void reverse(queue<int>& q){
    
    if(q.empty())
        return ;
        
    int num = q.front();
    q.pop();
    
    reverse(q);
    
    q.push(num);
    
}


queue<int> rev(queue<int> q)
{
    
    reverse(q);
    return q;
   
}

```