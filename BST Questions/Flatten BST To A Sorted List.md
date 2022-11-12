# Flatten BST To A Sorted List

```c++

void inorderTraversal( TreeNode<int>* root ,  vector< int >                                     &inorderVector)
{
   
    if( root == NULL )
            return ;
    
    inorderTraversal( root->left , inorderVector );
    
    inorderVector.push_back( root->data );
    
    inorderTraversal( root->right , inorderVector );
    
}
    
    


TreeNode<int>* flatten(TreeNode<int>* root)
{
    
    vector< int > inorderVector;
    inorderTraversal( root , inorderVector );
    
    int n  = inorderVector.size();
   
    // first node
    TreeNode<int>* firstNode = new TreeNode<int>( inorderVector[0] );
    TreeNode<int>* curr = firstNode;
    
    for( int i=1 ; i<n ; i++){
        
        TreeNode<int>* temp = new TreeNode<int>( inorderVector[i] );
        
        curr->left = NULL;
        curr->right = temp;
        curr = temp;
        
    }
    
    
    // last node
    curr->left = NULL;
    curr->right = NULL;
    
    return firstNode;
    
}


```