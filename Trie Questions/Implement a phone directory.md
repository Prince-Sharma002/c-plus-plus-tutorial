# Implement a phone directory

```c++


class TrieNode{
  
  public:
  char data;
  TrieNode* children[26];
  bool isTerminal;
  
  TrieNode( char d){
      data = d;
      isTerminal = false;
      for( int i=0 ; i<26 ; i++ ){
          children[i] = NULL;
      }  
  }

};




class Trie{
  
  public:
  TrieNode* root;
  Trie(){
      root = new TrieNode( '\0');
  }
  
  
  // insertion in Trie
  
    void insertUtil( TrieNode* root  , string word ){
      
      // base condition
      if( word.length() == 0 ){
          root->isTerminal = true;
          return ;
      }
      
      // Assumming that word is capitalize
      int index = word[0] - 'a';
      
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
    
    
    void printSuggestions( TrieNode* curr , vector<string> &ansStore , string prefix ){
     
        // base Condition - one word is found
        if( curr->isTerminal ){
            ansStore.push_back( prefix ) ;
        }
        
        
        for( char ch='a' ; ch <='z' ; ch++ ){
            
            // next is created to check all children of curr
            TrieNode* next = curr->children[ ch - 'a' ];
            
            
            if( next != NULL ){
                prefix.push_back(ch);
                
                // Recursion call
                printSuggestions( next , ansStore , prefix);
                prefix.pop_back();
            }
            
            
        }
        
    }
    
    
     vector<vector<string>> getSuggestions( string str ){
        
        TrieNode* prev = root;
        vector<vector<string>> output;
        string prefix = "";
        
        for( int i=0 ; i <str.length() ; i++ ){
            
            char lastch = str[i];
            prefix.push_back(lastch);
            
            // check if last character is in the trie
            TrieNode* curr = prev->children[ lastch - 'a' ];
            
                // lastch not found
            if( curr == NULL){
                break;
            }
                // lastch found
            else{
                
                // all suggestions at particular prefix will store in ansStore
                vector<string> ansStore;
                
                // printSuggestions Function call 
                printSuggestions( curr , ansStore , prefix );
                
                
                output.push_back( ansStore );
                ansStore.clear();
                prev = curr;
                
            }
       
        }
        
        return output;
        
    }
    
    
};
    

    
vector<vector<string>> phoneDirectory(vector<string>&contactList, string &queryStr)
{
    Trie *t = new Trie();
    
    // inserting Contacts in Trie
    for( int i=0 ; i<contactList.size() ; i++ )
        t->insertString( contactList[i] );
    
    
    return t->getSuggestions( queryStr ); 
    
}


```