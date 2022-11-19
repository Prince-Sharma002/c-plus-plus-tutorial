# K-th Largest Sum Subarray

```c++


int getKthLargest(vector<int> &arr, int k)
{
	priority_queue< int , vector<int> , greater<int> > pq;
    
    int n = arr.size();
    int sum;
    
    for( int i=0 ; i<n ; i++){
        
        sum = 0;
        
        for( int j=i ; j<n ; j++ ){
            
            sum += arr[j];
            
            if(pq.size() < k ){
               pq.push(sum); 
            }
            else {
                 if( sum > pq.top() ){
                    pq.pop();
                    pq.push( sum );
                 }
                
            }
            
        }
        
    }
    
    
    return pq.top();
}


```