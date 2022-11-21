# Median in a stream

```c++

#include <queue>

int signum( int maxisize , int minisize ){
    
    if( minisize == maxisize )
        return 0;
    else if ( maxisize > minisize )
        return 1;
    else  
        return -1;
    
}

void solve( int ele , priority_queue< int > &maxheap  , 
            priority_queue<  int , vector<int> , greater<int> > &minheap , int &median ){
    
   switch( signum( maxheap.size() , minheap.size() )  ){
    
       case 0 :
           if( ele > median ){
               minheap.push( ele );
               median = minheap.top();
           }
           else{
               maxheap.push( ele );
               median = maxheap.top();
           }
           break;
           
       case 1:
           if( ele > median ){
               minheap.push( ele );
               median = ( minheap.top() + maxheap.top() )/2;
           }
           else{
               minheap.push( maxheap.top() );
               maxheap.pop();
               maxheap.push( ele );
               median = ( minheap.top() + maxheap.top() )/2;
           }
           break;
       case -1:
           if( ele > median ){
               maxheap.push( minheap.top() );
               minheap.pop();
               minheap.push( ele );
               median = ( minheap.top() + maxheap.top() )/2;
           }
           else{
               maxheap.push( ele );
               median = ( minheap.top() + maxheap.top() )/2;
           }
           break;
            
   } 
   
    
}


vector<int> findMedian(vector<int> &arr, int n){
	
    vector<int> ans;
    priority_queue< int > maxheap;
    priority_queue<  int , vector<int> , greater<int> > minheap;
    int median = -1;
    
    for( int i=0 ; i<n ; i++){
        solve( arr[i] , maxheap , minheap , median );
        ans.push_back( median );
    }
	
    return ans;
}

```