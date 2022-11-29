# Detect Cycle In A Directed Graph
```c++

#include <bits/stdc++.h>


bool cycleCheck( unordered_map< int , vector<int> > &adj , unordered_map < int , bool > &isVisited
                , int node , unordered_map < int , bool > &dfsVisited )
{
    
    isVisited[ node ] = 1;
    dfsVisited[ node ] = 1;
    
    
    // inside for loop it will check if there is cycle present or not
    for( auto adjEle : adj[ node ] ){
        
       if( !isVisited[ adjEle ] )
       {
           bool cycleDetect =  cycleCheck( adj , isVisited , adjEle , dfsVisited );
           if( cycleDetect )
               return 1;
       }
       else
       {
           if( dfsVisited[ adjEle ] )
               return 1;
               
       }    
        
    }
    
    // 
    dfsVisited[ node ] = 0;
    return 0;
    
}    
    

int detectCycleInDirectedGraph(int n, vector < pair < int, int >> & edges) {
  
    // create adjacent list
    unordered_map< int , vector<int> > adj;
    
    for( int i=0 ; i< edges.size() ; i++ )
    {
        int u = edges[i].first;
        int v = edges[i].second;
        
        adj[u].push_back( v );
        
    }    
    
    
    unordered_map < int , bool > isVisited;
    unordered_map < int , bool > dfsVisited;
    
    for( int i=1 ; i<=n ; i++ )
    {
        if( !isVisited[i] ){
            int ans = cycleCheck( adj , isVisited , i , dfsVisited );
            if( ans == 1 )
                return 1; // cycle present
        }
    }
    
    // cycle not present 
    return 0;
    
    
}


```