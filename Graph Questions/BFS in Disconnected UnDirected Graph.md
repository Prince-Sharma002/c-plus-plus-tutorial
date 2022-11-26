# BFS in Disconnected UnDirected Graph 

```c++

#include <bits/stdc++.h> 

void bfs( unordered_map< int , set<int> > adj , unordered_map< int , bool > &isVisited  ,  vector<int> &ans ,  int node )
{
    queue<int> q;
    q.push( node );
    
    isVisited[ node ] = 1;
    
    while( !q.empty() ){
        int frontNode = q.front();
        q.pop();
        
        ans.push_back( frontNode );
        
        for( auto i : adj[ frontNode ] ){
            if( !isVisited[i] ){
                q.push( i );
                isVisited[i] = 1;
            }
        }
       
        
    }
}

vector<int> BFS(int vertex, vector<pair<int, int>> edges)
{
    // create adj list
    unordered_map< int , set<int> > adj;
    for( int i=0 ; i<edges.size() ; i++ ){
        
        int u = edges[i].first;
        int v = edges[i].second;
        
        adj[u].insert( v );
        adj[v].insert( u );
        
    }
    
    unordered_map< int , bool > isVisited;
    vector<int> ans;
    
    
    // For disconnected graph we use for loop and traverse all nodes
    for( int i=0 ; i<vertex ; i++ ){
        
        if( !isVisited[i] ){
            bfs( adj , isVisited , ans , i  );
        }
        
    }
    
    return ans;
    
}


```