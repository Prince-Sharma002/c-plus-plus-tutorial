#   Heapify Algorithm

```c++


void heapify( int arr[] , int n , int i ){
       
       int rootIndex = i ;
       
       int left = 2*i;              // left child index
       int right = 2*i + 1;         // right child index
       
       
       if( left < n &&  arr[rootIndex] < arr[left] ){
           rootIndex = left;
       }
       
       if( right < n && arr[rootIndex] < arr[right] ){
           rootIndex = right;
       }
       
       // rootIndex element is not at its correct place
       if( rootIndex != i){
           swap( arr[rootIndex] , arr[i] );
           
           // again apply heapify function on replaced parent element
           heapify( arr, n , rootIndex );
       }
       
}
    
    
int main(){
    
   
    int arr[8] = {-1 , 8 , 10 , 7 , 9 , 3, 2 , 1 };
    
    // n = size of array ( index based )
    int n = sizeof(arr)/sizeof(arr[0]) - 1;
     
     // applying heapify function on every element except leaf node
    for( int i = n/2 ; i>0 ; i-- ){
        heapify( arr , n , i );
    }
    
    
    // Printing array
    for( int i=1 ; i<=n ; i++ ){
        cout<< arr[i] << " ";
    }

}

```