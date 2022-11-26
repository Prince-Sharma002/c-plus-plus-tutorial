# DFS Traversal

```c++


#include <bits/stdc++.h>


void dfs( unordered_map < int , list<int> > &adj , unordered_map < int , bool > &isvisited  , 
          int node , vector<int> &component  )
{
          
    // add node in component
    component.push_back( node );
    
    // mark node to visited true
    isvisited[ node ] = 1;
    
    for ( auto i : adj[ node ] ){
        
        if( !isvisited[i] ){
            // recursion
            dfs( adj , isvisited , i , component );
        }
    }
    
          
}


vector<vector<int>> depthFirstSearch(int V, int E, vector<vector<int>> &edges)
{
    // create adj list 
    unordered_map < int , list<int> > adj;
    for( int i=0 ; i<edges.size() ; i++ ){
        int u = edges[i][0];
        int v = edges[i][1];
        
        adj[u].push_back( v );
        adj[v].push_back( u );
        
    }
    
    // create ans vector
    vector< vector < int >> ans;
    
    //create visited map
    unordered_map < int , bool > isvisited;
    
    for( int i=0 ; i<V ; i++ ){
        if( !isvisited[i] ){
            
            vector<int> component;
            dfs( adj , isvisited , i , component );
            
            // store component in final ans
            ans.push_back(component);
        }
        
    }
    
    return ans;
    
}


```