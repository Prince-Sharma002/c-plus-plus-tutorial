# Create Heap and Insertion using Array 

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
    
    h.print();

}


```