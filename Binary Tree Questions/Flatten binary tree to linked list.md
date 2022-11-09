# Flatten binary tree to linked list

```c++

void flatten(Node *root)
    {
        Node* curr = root;
        Node* prev = NULL;
        
        
        while( curr != NULL ){
            
            if( curr->left  ){
                
                prev = curr->left;
                while( prev -> right )
                    prev = prev->right;
                    
                prev-> right = curr->right;
                curr-> right = curr->left; 
                
            }
            
            curr = curr->right;
            
        }
        
        
        curr = root;
        
        while( curr != NULL )
        {
            
            curr->left = NULL;
            curr = curr -> right;
            
        }
        
        
}


```