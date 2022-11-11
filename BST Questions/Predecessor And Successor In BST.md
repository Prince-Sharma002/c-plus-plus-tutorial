# Predecessor And Successor In BST

```c++

pair<int,int> predecessorSuccessor( BinaryTreeNode<int>* root, int key)
{
    
    BinaryTreeNode<int>* temp = root;
    
    int pred = -1;
    int succ = -1;
    
    
    while( temp->data != key ){
        
    if( temp->data > key ){
        succ = temp->data;
        temp = temp->left;
    }
    else{
        pred = temp->data;
        temp = temp->right;
    }
        
    }
    
    // pred 
    BinaryTreeNode<int>* lefttree = temp->left;
    while( lefttree != NULL ){
        pred = lefttree->data;
        lefttree = lefttree -> right;
    }
    
    // succ
    
    BinaryTreeNode<int>* righttree = temp->right;
    while( righttree != NULL ){
        succ = righttree->data;
        righttree = righttree->left;
    } 
    
    
    pair< int , int > ans = make_pair(pred , succ );
    return ans;
    
}

```