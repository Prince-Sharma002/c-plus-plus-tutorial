# Valid Parentheses

```c++

bool isValidParenthesis(string expression)
{
  
    stack<char> s;
    
     for(int i=0 ; i< expression.length() ; i++){
         
         char ch = expression[i];
         
         if(ch == '(' || ch == '[' || ch == '{'){
             s.push(ch);
         }
         else{
             
             // if stack is empty you can use top function
             char top = ' ';
             if(s.empty() == false){
                 top = s.top();
             }
             
             if(ch ==')' && top == '('  )
                 s.pop();
         
             
             else if(ch ==']' && top == '[')
                 s.pop();
             
             
             else if (ch =='}' && top == '{')
                 s.pop();
             
             else 
                 return false;
          
             
         }

     }
    
    
    // if stack is not empty that means parentheses start but not closed  
    if(s.empty())
        return true;
    else
        return false;
    
    
}

```