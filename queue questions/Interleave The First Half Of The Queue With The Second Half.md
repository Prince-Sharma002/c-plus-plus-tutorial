#  Interleave The First Half Of The Queue With The Second Half

```c++

void interLeaveQueue(queue < int > & q) {
   
    
    queue< int > firstHalf; 
    int half = q.size()/2;
    // first half of queue is stored in another queue
    for(int i =0 ; i < half ; i++ ){
        
        firstHalf.push( q.front() );
        q.pop();
        
    }
    
    
    
    while( !firstHalf.empty() )
    {
        // push first element of both queue until firstHalf gets empty
        q.push( firstHalf.front() );
        q.push( q.front() );
        
        q.pop();
        firstHalf.pop();
    }
    
    
}


```