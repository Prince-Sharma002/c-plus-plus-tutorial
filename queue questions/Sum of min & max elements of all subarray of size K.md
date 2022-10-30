#  Sum of min & max elements of all subarray of size K

```c++

int solve(int arr[] ,  int k , int n){
    
    deque < int > maxi(k);
    deque < int > mini(k);
    
    
    // first k element processing
    for(int i=0 ; i<k ; i++){
        
        while( !maxi.empty() && arr[ maxi.back() ] <= arr[i] ){
            maxi.pop_back();
        }
        
        while( !mini.empty() && arr[ mini.back() ] >= arr[i] ){
            mini.pop_back();
        }
        
        maxi.push_back(i);
        mini.push_back(i);
        
    }
    
    
    // store ans
    int ans = 0;
    
    
    
    // remaining windows processing
    for( int i=k  ; i<n ; i++){
        
        ans += arr[ maxi.front() ] + arr[ mini.front() ];
        
        // removal of first element from window
        while( !maxi.empty() && i - maxi.front() >= k )
            maxi.pop_front();
            
        while( !mini.empty() && i - mini.front() >= k )
            mini.pop_front();
            
            
        
        //addition of element
        while( !maxi.empty() && arr[ maxi.back() ] <= arr[i] ){
            maxi.pop_back();
        }
        
        while( !mini.empty() && arr[ mini.back() ] >= arr[i] ){
            mini.pop_back();
        }
        
        maxi.push_back(i);
        mini.push_back(i);
      
    }
    
    // storing last window answer
    ans += arr[ maxi.front() ] + arr[ mini.front() ];
    
    return ans;
    
    
}

    
    
int main(){
    
    int arr[7] = { 2, 5 , -1 , 7 , -3 , -1 , -2 };
    int k = 4;
    int n = sizeof(arr)/sizeof(arr[0]);
    
    cout<< solve(arr , k , n) ;

}



```