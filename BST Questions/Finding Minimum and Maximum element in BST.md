# Finding Minimum and Maximum element in BST

```c++


// Function for Finding Minimum element in BST
int MininBST( node* root ){
    
    node* temp = root;

    // For Maximum element -   temp->right != NULL
    while( temp->left != NULL ){

         // For Maximum element -   temp = temp->right;
        temp = temp->left;
    }
    
    return temp->data;
  
}

```