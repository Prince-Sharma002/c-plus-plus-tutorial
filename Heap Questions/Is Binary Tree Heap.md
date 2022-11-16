#  

```c++


// NodeCount - count number of nodes in heap
int NodeCount( struct Node* tree ){
        
        if( tree == NULL )
            return 0;
            
        int ans =  1 +  NodeCount( tree->left ) + NodeCount( tree->right ) ;
        return ans;
}
  
  
  
// isBST - check if the Binary tree is complete bst 
bool isBST( struct Node* tree , int i , int n ){
    
    // base case  
    if(tree  == NULL)
        return true;
        
    
    // if index greater than total nodes it means its not complete bst    
    if( i >= n )
        return false;
    else{
        
        // for zero based indexing left child index is 2*i + 1 
        bool left = isBST( tree->left , 2*i + 1 , n );
        
        // for zero based indexing right child index is 2*i + 2 
        bool right = isBST( tree->right , 2*i + 2 , n );
        
        return left && right; 
    }
     
}
  
  
  
// isMaxOrder - check that parent node data is greater than its child data
bool isMaxOrder( struct Node* root ){
      
      
      // leaf node
    if( root->left == NULL && root->right == NULL )
        return true;
    
    // only left child node exist   
    if( root->right == NULL )
        return ( root->data > root->left->data );
    
    
    // both child exist  
    else{
        
        bool left = isMaxOrder( root->left );
        bool right = isMaxOrder( root->right );
        
        return left && right && ( root->data > root->left->data ) && ( root->data > root->right->data );
        
    }
     
}
  
  
// isHeap - return , is the Binary tree a heap or not  
bool isHeap(struct Node* tree) {
        
        int index = 0 ;
        int totalNodeCount = NodeCount( tree ) ;
        
        
        if( isBST( tree , index , totalNodeCount ) && isMaxOrder( tree ) )
            return true;
        else 
            return false;
        
        
}


```