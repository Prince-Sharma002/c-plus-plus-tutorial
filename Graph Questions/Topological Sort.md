# Topological Sort
```c++

#include <bits/stdc++.h> 

void topofxn( unordered_map < int , vector<int>  > &adj , unordered_map < int , bool > &isVisited 
              , int node ,  stack < int > &s)
{
    
    isVisited[ node ]  = 1;
    for( auto adjEle : adj[ node ]){
        
        if( !isVisited[ adjEle ])
            topofxn( adj , isVisited ,  adjEle , s );
        
    }
    
    // store element in stack
    s.push( node );
    
}
    
    
vector<int> topologicalSort(vector<vector<int>> &edges, int v, int e)  {
    
    // create adjacent list and store edges
    unordered_map < int , vector<int>  > adj;
    
    for( int i=0; i<e ; i++ )
    {
        int u = edges[i][0];
        int v = edges[i][1];
        
        adj[u].push_back( v );
        
    }
    
    unordered_map < int , bool > isVisited;
    stack < int > s;
    
    
    for( int i=0 ; i<v ; i++ ){
        
        if( !isVisited[i] )
            topofxn( adj , isVisited , i  , s );
        
    }
    
    // insert ans in ans vector
    vector< int > ans;
    while( !s.empty() )
    {
        ans.push_back( s.top() );
        s.pop();
    }    
    
    return ans;

}


```