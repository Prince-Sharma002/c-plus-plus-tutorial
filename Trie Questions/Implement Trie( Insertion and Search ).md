# Implement Trie( Insertion and Search )

```c++

class TrieNode{
  
  public:
  char data;
  TrieNode* children[26];
  bool isend;
  
  TrieNode( char d){
      data = d;
      isend = false;
      for( int i=0 ; i<26 ; i++ ){
          children[i] = NULL;
      }  
  }
    
    
};


class Trie{
  
  public:
  TrieNode* root;
  Trie(){
      root = new TrieNode(NULL);
  }
  
  
  // insertion in Trie
  
  void insertUtil( TrieNode* root  , string word ){
      
      // base condition
      if( word.length() == 0 ){
          root->isend = true;
          return ;
      }
      
      // Assumming that word is capitalize
      int index = word[0] - 'A';
      
      TrieNode* child ;
      
      // character is present
      if( root->children[index] != NULL ){
          child = root->children[index];
      }
      // insert new node
      else{
          child = new TrieNode(word[0]);
          root->children[index] = child;
      }
      
      // Recursion
      insertUtil( child , word.substr(1) );
    
}

  
void insertString( string word ){
    insertUtil( root , word);
}
  
  
  
// Search in Trie
  
bool SearchUtil( TrieNode* root , string word ){
      // base condition
      if( word.length() == 0  ){
          return root->isend;
      }
      
      int index = word[0] - 'A';
      TrieNode* child;
      
      // if present then proceed
      if( root->children[index] != NULL ){
          child = root->children[index]; 
      }
      // if not present return false
      else{
          return false;
      }

      return SearchUtil( child , word.substr(1) );
      
  }
  
bool isPresent( string word){
    return SearchUtil( root , word );
}
     
};

    
    
int main(){
    
    Trie *t = new Trie();
    
    t->insertString("ABC");
    
    cout<< t->isPresent("ABCD");
   
}


```