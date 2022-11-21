# Smallest Range From K Sorted List

```c++

#include <queue>

// creating node class
class node{
  
    public:
    int data;
    int rowIndex;
    int colIndex;
    
    node( int d , int row ,  int col){
        data = d;
        rowIndex = row;
        colIndex = col;
    }
    
};


class compare{
    public:
    bool operator()( node* a , node* b){
        return a->data > b->data;
    }
};



int kSorted(vector<vector<int>> &a, int k, int n) {
    
    int mini = 0 , maxi = 0;
    
    // creating min heap
    priority_queue< node* , vector<node*> , compare > minHeap; 
    
    // insertng first element of every linked list
    for( int i=0 ; i<k ; i++ ){
        int ele = a[i][0];
        mini = min(mini , ele);
        maxi = max(maxi , ele);
        minHeap.push( new node(ele , i , 0) );
    }
    
    
    int start = mini , end = maxi;
    
    
    while( minHeap.size() > 0 ){
        
        // accessing minimum element of min heap
        node* temp = minHeap.top();
        minHeap.pop();
        
        mini = temp->data;
        
        // compare range 
        if( maxi - mini < end - start ){
            start = mini;
            end = maxi;
        }
        
        // inserting next node of pop element 
        if( temp->colIndex + 1 < n ){
            maxi = max( maxi ,  a[temp->rowIndex][temp->colIndex + 1]  );
            minHeap.push( new node( a[temp->rowIndex][temp->colIndex + 1] , 
                                   temp->rowIndex , temp->colIndex +1) );
        }
        // if linked list completed then break 
        else
            break;
      
    }
    
    return end - start + 1 ;
}

```