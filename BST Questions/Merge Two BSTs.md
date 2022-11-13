# Merge Two BSTs

```c++

// BST to Vector function
void inorderTraversal( TreeNode<int>* root ,  vector< int >                                     &inorderVector)
{
   
    if( root == NULL )
            return ;
    
    inorderTraversal( root->left , inorderVector );
    
    inorderVector.push_back( root->data );
    
    inorderTraversal( root->right , inorderVector );
    
}


// Merge Two Vector in Sorted order
vector<int> mergeVec( vector<int> &vec1 , vector<int> &vec2 ){
    
    vector<int> ans( vec1.size() + vec2.size() );
    
    int i=0  , j=0 , k=0 ;
    
    while( i < vec1.size() && j < vec2.size() ){
        
        if( vec1[i] < vec2[j] ){
            ans[k++] = vec1[i];
            i++;
        }
            
        else{
            ans[k++] = vec2[j];
            j++;
        }
            
        
    }
    
    while( i < vec1.size() ){
        ans[k++] = vec1[i];
        i++;
    }
        
    
    while( j<vec2.size() ){
        ans[k++] = vec2[j];
        j++;
    }
        
   
    
    return ans;
    
}


// vector to Bst Function
TreeNode<int>* inorderToBST( int s  , int e , vector<int> &inorderVal ){
    
    if( s>e )
        return NULL;
    
    int mid = (s+e)/2;
    
    TreeNode<int>* root = new TreeNode<int>( inorderVal[mid] );
    
    root->left = inorderToBST( s , mid -1 , inorderVal);
    root->right = inorderToBST( mid+1 , e , inorderVal);
    return root;
    
    
}



TreeNode<int> *mergeBST(TreeNode<int> *root1, TreeNode<int> *root2){
    
    vector<int> vec1;
    vector<int> vec2;
    
    inorderTraversal( root1 , vec1 );
    inorderTraversal( root2 , vec2 );
    
    
    vector<int> mergeVector = mergeVec( vec1 , vec2 );
    
    int s=0 , e = mergeVector.size()-1;  
    
    return inorderToBST( s , e , mergeVector );
   
    
}


```