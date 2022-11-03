#  Diameter of a Binary Tree

```c++

int height(struct Node* node){
        
        if(node == NULL)
            return 0;
            
        
        int left = height(node->left);
        int right = height(node->right);
        
        
        int ans = max(left , right) +  1;
        return ans;
        
}


int diameter(Node* root) {
        
        if(root == NULL)
            return 0;
            
        int left = diameter(root ->left);
        int right = diameter(root->right);
        int mixed = height(root->left) + height(root->right) + 1;
        
        int ans = max( left , max(right , mixed) );
        return ans ;
        
}


```