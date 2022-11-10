# Implementation of BST ( Binary Search Tree )

```c++

class node{
  
  public:
  int data;
  node* left;
  node* right;
  
  node(int d){
      
      this->data  = d;
      this->left = NULL;
      this->right = NULL;
      
  }
    
};


// inorder traversal
void inorder(node* root){
    
    if(root ==  NULL){
        return ;
    }
    
    inorder( root -> left );
    cout << root->data;
    inorder( root-> right );
   
}

// insertion in bst
node* insertInBST( node* &root , int data ){
    
    
    if( root == NULL ){
        root = new node( data );
        return root;
    }
    
    if( root->data < data ){
        root->right = insertInBST( root->right , data );
    }
    else{
        root->left = insertInBST( root->left , data );
    }
    
    return root;
    
}

// take input from user
void takeInput( node* &root ){
    
    int data ;
    cin >> data;
    
    // take input from user till input is not equal to -1
    while( data != -1 ){
        
        insertInBST( root , data );
        cin >> data;
        
    }
    
    
}

 
    
int main(){
    
    node* root = NULL;
    
    cout<< "Enter data inside bst :" << endl;
    takeInput( root);
    
    cout<< "Printing bst in inorder traversal" << endl;
    inorder( root );
    

}


```