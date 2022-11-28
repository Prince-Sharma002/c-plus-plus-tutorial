# Cycle Detection In Disconnected Undirected Graph

```c++

#include <bits/stdc++.h>

bool checkCycle( unordered_map < int , vector< int >  > adj ,unordered_map < int , bool > &isVisited ,
                 int node )
{
    queue<int> q;
    unordered_map < int , int  >  parent;
    
    parent[ node ] = -1 ;
    q.push( node );
    isVisited[ node ] = 1;
    
    while( !q.empty() ){
        
        int frontNode = q.front();
        q.pop();
        
        for( auto adjEle : adj[ frontNode ]  ){
            
            // cyclic present
            if( adjEle != parent[ frontNode ] && isVisited[adjEle] == 1 )
                return true;
            
            // insert element
            else if( isVisited[ adjEle ]  != 1  ){
                q.push( adjEle );
                isVisited[ adjEle ] = 1;
                parent[ adjEle ] = frontNode;
            }
            
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
    
    // due to disconnected graph we need to traverse all element 
    for(  int i=0 ; i<n ; i++ ){
        if( !isVisited[i]  ){
            
            bool ans = checkCycle( adj , isVisited , i );
            if ( ans == 1)
                return "Yes";
            
            
        }
    }
    
    return "No";
}


```