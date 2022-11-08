# Construct Tree from Inorder & Preorder

```c++

    void createMap( int in[] , int n , map<int , int> &nodeToIndex ){
        
        for( int i=0 ; i<n ; i++ ){
            nodeToIndex[ in[i] ] = i;
        }
        
    }


    
    Node* solve( int in[] , int pre[] , int &index , int inorderStart , int inorderEnd ,
                map<int , int> &nodeToIndex , int n  ){
                    
                    
        if( index >= n || inorderStart > inorderEnd)
            return NULL;
            
            
        int element  = pre[ index++ ];
        Node* root = new Node( element );
        int pos = nodeToIndex[ element ];
        
        root -> left = solve( in , pre , index , inorderStart , pos-1 , nodeToIndex , n );
        root -> right = solve( in , pre , index , pos+1 , inorderEnd , nodeToIndex , n );
        
        
        return root;
                  
    }
    
    
    Node* buildTree(int in[],int pre[], int n)
    {
       
       int preOrderIndex = 0;
       map < int , int > nodeToIndex ;
       
       createMap( in , n , nodeToIndex );
       Node* ans =  solve( in , pre , preOrderIndex , 0 , n-1 , nodeToIndex , n );
       
       return ans;
       
    }
```