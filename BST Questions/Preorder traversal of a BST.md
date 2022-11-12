# Preorder traversal of a BST

```c++


BinaryTreeNode<int>* solve( vector<int> &preorder , int min , int max , int &i ){
    
    if( i >= preorder.size() )
        return NULL;
    
    if( preorder[i] < min || preorder[i] > max )
        return NULL;
    
    BinaryTreeNode<int>* node = new BinaryTreeNode<int>( preorder[i++] );
    node->left = solve( preorder , min , node->data , i );
    node->right = solve( preorder , node->data , max , i );
    
    return node;
    
}



BinaryTreeNode<int>* preorderToBST(vector<int> &preorder) {
    int min = INT_MIN;
    int max = INT_MAX;
    
    int i = 0;
    return solve( preorder , min , max , i );
    
}



```