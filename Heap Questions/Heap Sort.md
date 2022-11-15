#   Heap Sort

```c++

void heapSort( int arr[] ,int n ){
    
    int s = n;
    while( s > 1 ){
        swap(arr[1] , arr[s]);
        s--;
        
        heapify(arr , s , 1);
    }
    
}

```