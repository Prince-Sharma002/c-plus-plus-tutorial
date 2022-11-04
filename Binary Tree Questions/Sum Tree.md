# Sum Tree

```c++
pair<bool , int >  checkSumTree(Node* root){
        
        // base case
        if(root == NULL){
            
            pair< bool , int > p = make_pair(true , 0);
            return p;
            
        }
        
        
        // if leave node return true and node data
        if( root->left == NULL && root->right == NULL ){
            
            pair< bool , int > p = make_pair(true , root->data);
            return p;
            
        }
        
        
        
        pair<bool , int > leftnode = checkSumTree( root->left );
        pair<bool , int > rightnode = checkSumTree( root->right );
        
        
        bool left = leftnode.first;
        bool right = rightnode.first;
        
        
        // check sum tree condition
        bool cond = root->data == leftnode.second + rightnode.second;
        
        pair < bool , int > ans;
        
        if(left && right && cond){
            
            ans.first = true;
            
            // store left and right sum tree plus root->data 
            ans.second = 2*root->data;
            
        }
        
        else{
            
            ans.first = false;
            
        }
        
        return ans;
      
}



bool isSumTree(Node* root)
    {
         return checkSumTree(root).first;
    }

```