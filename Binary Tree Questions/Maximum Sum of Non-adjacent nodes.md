# Maximum sum of Non-adjacent nodes

```c++

//Function to return the maximum sum of non-adjacent nodes.
    
    pair< int , int >  solve( Node* root  ){
      
      if( root == NULL ){
          
          pair <  int , int >  p = make_pair( 0 , 0 );
          return p;
           
      }
       
       pair< int  , int > left  = solve(  root->left );
       pair< int  , int > right = solve(  root->right);
       
       pair< int , int > res;
       
       // include root element and add with exclude left and right nodes
       res.first = root->data + left.second + right.second;
       
       // max from left node first and second element , and from right node first and second element
       res.second = max( left.first , left.second ) + max( right.first , right.second );
       
       return res;
       
     
  }
    
    int getMaxSum(Node *root) 
    {
       
       pair< int , int >  ans = solve(root);
       
       // answer is max from root node left and right element
       return max( ans.first , ans.second);
       
       
    }

```