#  Max rectangle

```c++

class Solution{
    
private:

vector<int> nextSmallerElement(int* arr, int n)
{
    
    stack<int> st;
    st.push(-1);  
    
 
    vector<int> ans(n);
    
    for(int i = n-1  ;  i >= 0  ;  i--){
        
        int current_element = arr[i];
        
    
        while( st.top() != -1 &&  arr[st.top()] >= current_element ){
            st.pop();
        }
            
     
        ans[i] = st.top();
        st.push(i);
 
    }
    
    return ans;
  
}
    
    
vector<int> prevSmallerElement(int* arr, int n)
{
    
    stack<int> st;
    st.push(-1);  
    
 
    vector<int> ans(n);
    
    for(int i = 0  ;  i < n  ;  i++){
        
        int current_element = arr[i];
        
    
        while( st.top() != -1 &&  arr[st.top()] >= current_element ){
            st.pop();
        }
            
     
        ans[i] = st.top();
        st.push(i);
 
    }
    
    return ans;
  
}


int largestRectangleArea(int* heights , int n) {
        
       vector<int> next = nextSmallerElement(heights , n);
       vector<int> prev = prevSmallerElement(heights , n);
        
        int area = INT_MIN;
        
    
        for(int i=0 ; i<n ; i++){
            
            int l = heights[i];
            
            if(next[i] == -1)
                next[i] = n;
            
            int b = next[i] - prev[i] - 1;
            
            int newArea = l*b;
            area = max(newArea , area);
            
        }
        
        
        return area;
     
    }

    
    
  public:
    int maxArea(int M[MAX][MAX], int n, int m) {
       
       // compute area for first row
       int area = largestRectangleArea(M[0]  , m);
       
       // create histogram by adding each row
       for(int i=1 ; i<n ; i++){
           for(int j=0 ; j<m ; j++){
               
               if(M[i][j] != 0)
                M[i][j] = M[i][j] + M[i-1][j];
               else
                M[i][j] = 0;    
               
           }
           
           // find max area of histogram
           area = max(area , largestRectangleArea(M[i]  , m));
           
       }
       
       return area;
       
    }
};

```