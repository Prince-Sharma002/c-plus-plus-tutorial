#  Kth smallest element in Heap

```c++

int kthSmallest(int arr[], int l, int r, int k) {
        
        priority_queue<int> pq;
        
        // inserting first k element of array
        for( int i=0 ; i<k ; i++ ){
            pq.push( arr[i] );
        }
        
        // check element greater than heap top element
        for( int i=k ; i <= r ; i++){
            
            if( arr[i] < pq.top() ){
                pq.pop();
                pq.push( arr[i] );
            }
            
        } 
        
        
        return pq.top() ;
        
}

// time complexity - o( nlog(k))
// space complexity - 0(k)

```
