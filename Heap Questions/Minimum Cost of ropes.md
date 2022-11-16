# Minimum Cost of ropes

```c++


long long minCost(long long arr[], long long n) {
        
        // creating Min Heap
        priority_queue< long long , vector<long long> , greater<long long> > pq;
        
        for( int i=0 ; i<n ; i++ )
            pq.push( arr[i] );
            
            
        long long cost = 0;
        
        while( pq.size() > 1){
            
            // first smallest element
            long long a = pq.top();
            pq.pop();
            
            // second smallest element
            long long b = pq.top();
            pq.pop();
            
            long long sum = a + b;
            cost += sum;
            
            pq.push( sum );
            
        }
        
        return cost;
        
        
}


```