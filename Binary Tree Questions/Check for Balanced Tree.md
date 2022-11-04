#  Check for Balanced Tree

```c++

pair< bool , int > checkBalance(Node* root){
        
        
        // base case
        if(root == NULL){
            pair< bool , int > p = make_pair(true , 0);
            return p;
        }
        
        pair< bool , int > left =  checkBalance(root->left);
        pair< bool , int > right = checkBalance(root->right);
        
        bool leftAns = left.first;
        bool rightAns = right.first;
        
        // diff variable check condition of balance tree 
        bool diff = abs( left.second - right.second ) <= 1;
        
        
        pair<bool , int> ans;
        
        // store height of
        ans.second = max(left.second , right.second) + 1;
        
        
        // if condition are true , that node is balance
        if(leftAns && rightAns && diff){
            ans.first = true;
        }
        else{
            ans.first = false;
        }
        
        return ans;
        
        
        
}


bool isBalanced(Node *root)
    {
  
        return checkBalance(root).first;
 
    }


```