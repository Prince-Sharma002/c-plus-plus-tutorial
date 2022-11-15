#   Insertion and Deletion in Heap Using Array

```c++

class heap{
  
  public:
   int arr[50];
   int size;
   
   heap(){
       arr[0] = -1;
       size = 0;
   }
   
   // Time complexity - o( logn ) in insertion
   void insert( int d){
       size++;
       int index = size;
       arr[index] = d;
       
       // place insert element to its correct position
       while( index > 1 ){
           int parent = index/2;
           
           if(arr[parent] < arr[index]){
               swap( arr[parent] , arr[index] );
               index = parent;
           }
           else{
               return ;
           }
           
       }
       
   }
   
   
void deletion(){
       
       // if empty heap return
       if( size == 0 ){
           cout<< "empty heap";
           return ;
       }
        
       // replace root elememt with last element 
       arr[1] = arr[size];
       size--;
       

       int i = 1;

       // place root element to its correct position
       while( i < size ){
           
           int leftNode = i*2;
           int rightNode = ( i*2 ) + 1;
           
           if( leftNode < size && arr[leftNode] > arr[i] ){
               swap( arr[leftNode] , arr[i] );
               i = leftNode;
           }
           else if( rightNode < size && arr[rightNode] > arr[i] ){
               swap(arr[rightNode] , arr[i] );
               i = rightNode;
           }
           else{
               return ;
           }
          
       }
       
   }
   
   
   void print(){
       for(int i=1 ; i<=size ; i++)
            cout<< arr[i] << " ";
   }
    
};
 

    
int main(){
    
    heap h;
    h.insert(50);
    h.insert(57);
    h.insert(60);
    h.insert(40);
    
    h.deletion();
    
    h.print();

}

```