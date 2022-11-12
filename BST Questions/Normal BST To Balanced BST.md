# Normal BST To Balanced BST

```c++



void inorderTraversal( TreeNode<int>* root ,  vector< int >                                     &inorderVector)
{
   
    if( root == NULL )
            return ;
    
    inorderTraversal( root->left , inorderVector );
    
    inorderVector.push_back( root->data );
    
    inorderTraversal( root->right , inorderVector );
    
}

TreeNode<int>* inorderToBST( int s  , int e , vector<int> inorderVal ){
    
    if( s>e )
        return NULL;
    
    int mid = (s+e)/2;
    
    TreeNode<int>* root = new TreeNode<int>( inorderVal[mid] );
    
    root->left = inorderToBST( s , mid -1 , inorderVal);
    root->right = inorderToBST( mid+1 , e , inorderVal);
    return root;
    
}



TreeNode<int>* balancedBst(TreeNode<int>* root) {
    
    vector< int > inorderVector;
    inorderTraversal( root , inorderVector );
    
    int n  = inorderVector.size();
    
    return inorderToBST( 0 , n-1  , inorderVector);
    
}

```