#  First negative integer in every window of size k

```c++

vector<long long> printFirstNegativeInteger(long long int A[],
                                             long long int N, long long int K) {
                                                 
                                                 
        
    deque < int > dq;
    vector < long long int > ans;
    
    // first k element preocessing
    for(int i=0 ; i<K ; i++){
        
        if( A[i] < 0 ){
            dq.push_back(i);
        }
        
    }
    
    // store ans of first k element window
    if( dq.size() != 0 ){
        ans.push_back(A[ dq.front() ]);
    }
    else{
        ans.push_back(0);
    }
    
    
    
    // processing remaining windows
    for(int i=K ; i<N ; i++){
        
        // removal of element -  pop if only first element of window
        if( !dq.empty() && i-dq.front() >= K ){
            dq.pop_front();
        }
        
        // addition - if only negative number
        if( A[i] < 0 ){
            dq.push_back(i);
        }
        
        // ans store
        if( dq.size() != 0 ){
            ans.push_back(A[ dq.front() ]);
        }
        else{
            ans.push_back(0);
        }
        
        
    }
         
         return ans;                                        
                                                 
 }


```