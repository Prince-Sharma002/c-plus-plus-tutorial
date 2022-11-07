# Sum of the Longest Bloodline of a Tree

```c++

// maxSum and maxlen needs to pass by reference    
void solve( Node* root , int sum  , int &maxSum , int len , int &maxlen )
{
    
    // base case
    
    if( root == NULL ){
        
        
        if(len > maxlen){
            
            maxlen = len;
            maxSum = sum;
            
        }
        else if( len == maxlen ){
            
            maxSum = max(sum , maxSum);
            
        }
        
        return ;
       
    }
    
    
    sum =  sum + root->data;
    
    
    solve( root->left , sum , maxSum , len+1 , maxlen );
    solve( root->right , sum , maxSum , len+1 , maxlen );
   
    
}    
    
    
    
int sumOfLongRootToLeafPath(Node *root)
    {
        if(root == NULL)
            return 0;
            
            
        int sum = 0 ;
        int maxSum = INT_MIN;
        
        int len = 0 ;
        int maxlen = 0 ;
        
        solve( root , sum , maxSum , len , maxlen );
        
        return maxSum;
        
}


```