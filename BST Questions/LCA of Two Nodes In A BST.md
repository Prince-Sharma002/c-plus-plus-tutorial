# LCA of Two Nodes In A BST

```c++

TreeNode<int>* LCAinaBST(TreeNode<int>* root, TreeNode<int>* P, TreeNode<int>* Q)
{
	if( root == NULL )
        return root;
   
    
    if( root->data > P->data && root->data > Q->data ){
        return LCAinaBST( root->left , P , Q );
    } 
    
    if( root->data <  P->data && root->data < Q->data ){
        return LCAinaBST( root->right , P , Q );
    } 
    
    
    return root;
    
}

```