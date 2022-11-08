# Construct Tree from Inorder & Postorder

```c++

void createMap( int in[] , int n , map<int , int> &nodeToIndex ){
        
        for( int i=0 ; i<n ; i++ ){
            nodeToIndex[ in[i] ] = i;
        }
        
}



Node* solve( int in[] , int post[] , int &index , int inorderStart , int inorderEnd ,
                map<int , int> &nodeToIndex , int n  ){
                    
                    
        if( index <  0 || inorderStart > inorderEnd)
            return NULL;
            
            
        int element  = post[ index-- ];
        Node* root = new Node( element );
        int pos = nodeToIndex[ element ];
        
        
        root -> right = solve( in , post , index , pos+1 , inorderEnd , nodeToIndex , n );
        root -> left = solve( in , post , index , inorderStart , pos-1 , nodeToIndex , n );
       
        
        
        return root;
                    
                   
}

Node *buildTree(int in[], int post[], int n) {
    
    
       int postOrderIndex = n-1;
       map < int , int > nodeToIndex ;
       
       createMap( in , n , nodeToIndex );
       Node* ans =  solve( in , post , postOrderIndex , 0 , n-1 , nodeToIndex , n );
       
       return ans;
    
}

```