# Cycle Detection In Disconnected Undirected Graph ( using DFS )

```c++

#include <bits/stdc++.h>

bool checkCycle( unordered_map < int , vector< int >  > adj , unordered_map < int , bool                 > &isVisited  , int node , int parent )
{
    
        isVisited[ node ] =  1;
        for( auto adjEle : adj[ node ]){
            if( !isVisited[ adjEle ] )
            {
                
                 bool cycleDetect  = checkCycle( adj , isVisited , adjEle , node );
                if( cycleDetect  )
                    return true;
            }
            else if( adjEle != parent )
            {
                return true;
            }
        }
    
    return false;
}

string cycleDetection (vector<vector<int>>& edges, int n, int m)
{
    // create adjacen list
    unordered_map < int , vector< int >  > adj;
    for( int i=0 ; i<m ; i++ ){
        
        int u = edges[i][0];
        int v = edges[i][1];
        
        adj[u].push_back( v );
        adj[v].push_back( u );
        
    }
    
    unordered_map < int , bool > isVisited;
    unordered_map < int , int >  parent;
    
    // due to disconnected graph we need to traverse all element 
    for(  int i=0 ; i<n ; i++ ){
        if( !isVisited[i]  ){
            
            bool ans = checkCycle( adj , isVisited , i , -1);
            if ( ans == 1)
                return "Yes";
            
            
        }
    }
    
    return "No";
}


```