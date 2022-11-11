# Two Sum IV - Input is a BST

```c++


void inorderVector( BinaryTreeNode<int>* root , vector< int > &inorder ){
    
    if( root == NULL )
          return ;
    
    inorderVector( root->left , inorder );
    
    inorder.push_back( root->data );
    
    inorderVector( root->right , inorder );
   
}



bool twoSumInBST(BinaryTreeNode<int>* root, int target) {
	
    vector< int > inorder;
    inorderVector( root , inorder );
    
    int forw = 0;
    int back = inorder.size() - 1;
    
    while( forw != back ){
        
        int forwNode = inorder[forw];
        int backNode = inorder[back];
        
        if( forwNode + backNode  == target )
            return true;
        
        if( forwNode + backNode < target ){
            forw++;
        }
        else
            back--;
        
    }
    
    return false;
    
}

```