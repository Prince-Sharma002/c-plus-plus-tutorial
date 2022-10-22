#  The Celebrity Problem

```c++

int celebrity(vector<vector<int> >& M, int n) 
    {
        
        
        stack<int> st;
        
        
        // store all elements in stack
        for(int i=0 ; i<n ; i++){
            st.push(i);
        }
        
        
    int a;
    int b;
    
    while(st.size() != 1){
            
            a = st.top();
            st.pop();
            b = st.top();
            st.pop();
            
            
            // check if a knows b then push b and vice-versa
            if( M[a][b] == 1)
                st.push(b);
            else
                st.push(a);
        }
    
    // last element left in stack have potential to become celebrity
    int c = st.top();
    
    
    for(int i=0 ; i<n ; i++){
        
        
        // celebrity row should be filled with zero
        if(M[c][i] != 0)
            return -1;
            
        // all elements except celebrity itself should know celebrity
        if(c != i){
            if(M[i][c] != 1)
                return -1;
        }    
        
    }
    
    
    
    return c;
        
       
    }

```