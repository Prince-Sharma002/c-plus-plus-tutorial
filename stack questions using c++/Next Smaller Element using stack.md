# Next Smaller Element using stack

```c++
// NOTE : Not for negative element array

vector<int> nextSmallerElement(vector<int> &arr, int n)
{
    
  // creating stack
    stack<int> st;
    st.push(-1);   // -1 if no smaller number found
    
    // answer store in vector 
    // advantage of vector is you can store element at any location even start from end 
    vector<int> ans(n);
    
    for(int i = n-1  ;  i >= 0  ;  i--){
        
        int current_element = arr[i];
        
        // until st.top is greater simply pop top element
        while( st.top() >= current_element ){
            st.pop();
        }
            
        // after while loop ends top element definitely smaller than current element 
        ans[i] = st.top();
        st.push(current_element);
 
    }
    
    return ans;
 
    
}

```