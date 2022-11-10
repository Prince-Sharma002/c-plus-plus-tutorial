# Delete of node in BST

```c++


int maxnode( node* root ){
    
    node* temp = root;

    
    while( temp->right != NULL )
        temp = temp->right;
    
    
    return temp->data;
  
} 

node* deleteInBST( node* &root , int x  ){
    
    if( root == NULL)
        return root;
    
    
    if( root -> data == x ){
        
        // case 1 - if delete node have no child(leave node)
        if( root->left == NULL && root->right == NULL ){
            delete root;
            return NULL;
        }
        
        // case 2 - if there is only one child of delete node
        if( root->left != NULL && root->right == NULL ){
            node* temp =  root->left;
            delete root;
            return temp;       
        } 
        
        if( root->right != NULL && root->left == NULL ){
            node* temp =  root->right;
            delete root;
            return temp;   
        }
        
        // case 3 - if both child exist of delete node
        if( root->left != NULL && root->right != NULL ){
            int max = maxnode( root->left ) ;
            root->data  = max;
            root->left = deleteInBST( root->left , max );
            return root;
        } 
        
        
    }
    else if(  root->data > x  ){
        
        root->left  = deleteInBST( root->left  , x);
        return root;
        
    }
    else{
        
        root->right  = deleteInBST( root->right  , x);
        return root;
        
    }

}

```